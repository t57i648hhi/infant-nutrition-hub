# 生信分析|DNA甲基化显著波动位点分析-探究表观遗传变

> 更新时间：2026-09-11 (UTC+8)

导语

DNA甲基化是表观遗传学研究的重要组成，主要参与胚胎发育、基因印记、X染色体失活等过程，在正常的细胞发育和维持组织稳定性方面有着重要的作用机制。但异常的DNA甲基化也可能导致疾病、肿瘤的发生，因此检测DNA甲基化或许能在疾病诊断、预防、治疗中起到重要作用。

常用的DNA甲基化研究方法包括850K芯片、WGBS、RRBS、MeDIP以及甲基化靶向测序等，其中应用芯片这个高通量手段检测基因组的甲基化，具有单碱基识别、低起始量、重复性高等优点，为此Illumina推出Illumina DNA甲基化芯片。其中新一代的甲基化芯片-850K可检测人全基因组约853,307个CpG位点的甲基化状态，850K芯片不但保持了对CpG岛，基因启动子区的全面覆盖，还特别加强了增强子区以及基因编码区的探针覆盖。广泛应用于干细胞研究、肿瘤和其他复杂疾病研究，是目前最适合表观基因组全关联分析研究的全基因组DNA甲基化芯片。

癌症是一种异质性疾病，有研究表明[1]，甲基化变异性增加可能有助于其异质性，癌症表观遗传异质性的增加可能是癌细胞快速适应变化环境能力的基础。陆续也有不少研究[2-5]观察到正常样本之间一致的甲基化和癌症样本之间高度可变的甲基化，因此，识别甲基化位点变异性可能与理解疾病表型的差异甲基化一样重要，可以更好地理解肿瘤的发生。然而，在分析DNA甲基化数据时，目前主要关注的是组内变异性小而组间均值差异大的显著差异甲基化位点(Differential Methylation CpGs Positions，DMP)，每组内的测量结果往往相当一致。本文主要给大家介绍探究甲基化变异性的分析方法-DNA甲基化显著波动位点（Differentially variable CpG position, DVP）分析，也叫变异性甲基化位点分析。DVP指的是组间变异性显著差异的位点，是指其中一组样品的甲基化值一致，而另一组样品的甲基化值高度变化的位点。在做DNA甲基化的关联分析时，DMP的结果有时可能不尽人意，而DVP的分析或许能给我们带来新的思路与结果，成为甲基化以后的研究热点。
方法简述
DMP是计算组间DNA甲基化平均值的差异。而DVP是一种基于组间数据的变异程度，通过计算方差的分析方法，观测DNA甲基化β值的“波动”性，发现DMP分析无法找到的CpGs。对于复杂疾病，常见的t检验或回归方程，难以得到差异显著的且有意义的位点，此时推荐同时使用DVP分析方法。

晶能针对DVP分析主要是采取了比较经典的方法-DiffVar[6]，DiffVar是一种测试样本间DVP位点的方法，相较于F检验和Bartlett检验对异常值的高度敏感，DiffVar采用经典贝叶斯框架，对异常值具有鲁棒性。最后还有对得到的显著变异位点对应的基因做GO、KEGG、代谢等功能分析，探究DVP与疾病的关系。
结果展示
结果主要包括DiffVar分析的DVP位点表格（位点信息、P值以及数据库注释等等）、Top10位点散点图和DVP相关基因的功能分析，帮助大家更好的挖掘DVP与疾病的关系。

2.1 DVP位点表格

diffvar分析结果(diffvar_all_* _vs_* _BHadjust.txt)

2.2 DVP Top10位点散点图

选取diffvar分析p值最小的10个位点作散点图。

2.3 功能分析

针对diffvar分析的·DVP相关基因集，进行GO功能（TopGO软件）、KEGG通路（KEGG数据库）、Disease功能注释（DisGeNET疾病数据库）、Reactome通路（Reactome数据库）以及蛋白互作（STRING 数据库）等分析。

此功能分析和常规测序中的结果一致，故在此不多加赘述。
文章案例
Ⅰ型糖尿病中三种免疫效应细胞的DNA甲基化变异性增加[7]

发表期刊：Nature Communications

影响因子：17.694

文章链接：Increased DNA methylation variability in type 1 diabetes across three immune effector cell types

1型糖尿病(T1D)的发病率在过去十年中大幅增加，这表明非遗传因素如表观遗传机制在疾病发展中发挥了重要作用。在这里，作者提出了一项表观基因组全关联研究，研究对象是52对三种免疫效应细胞类型中T1D不一致的同卵双胞胎的406,365个CpGs。观察到T1D双胞胎的DVPs与健康的同卵双胞胎和健康的不相关个体相比显著增加。这些T1D相关的DVP被发现是暂时性稳定的，并且在基因调控元件上富集。通过对DVP相关基因进行功能富集分析发现主要参与免疫细胞代谢和细胞周期的途径，包括mTOR信号通路。来自显性T1D新生儿脐带血的证据表明，DVP可能在出生后出现。该结果表明表观遗传变化可能有助于T1D的疾病发生。
DMP和DVP分析结果
参考文献

1. Hansen KD, Timp W, Bravo HC, Sabunciyan S, Langmead B, McDonald OG, Wen B, Wu H, Liu Y, Diep D, Briem E, Zhang K, Irizarry RA, Feinberg AP: Increased methylation variation in epigenetic domains across cancer types. Nat Genet 2011, 43:768–775.

2. Feinberg AP, Irizarry RA: Evolution in health and medicine Sackler colloquium: stochastic epigenetic variation as a driving force of development, evolutionary adaptation, and disease. Proc Natl Acad Sci USA 2010, 107:1757–1764.

3. Feinberg AP, Irizarry RA, Fradin D, Aryee MJ, Murakami P, Aspelund T, Eiriksdottir G, Harris TB, Launer L, Gudnason V, Fallin MD: Personalized epigenomic signatures that are stable over time and covary with body mass index. Sci Transl Med 2010, 2:49ra67.

4. Issa J-P: Epigenetic variation and cellular Darwinism. Nat Genet 2011, 43:724–726.

5. Jaffe AE, Feinberg AP, Irizarry RA, Leek JT: Significance analysis and statistical dissection of variably methylated regions. Biostatistics 2012, 13:166–178.

6. Phipson, B. Oshlack, A. DiffVar: a new method for detecting differential variability with application to methylation in cancer and aging. Genome Biol. 15, 465 (2014).

7. Paul DS. et al. Increased DNA methylation variability in type 1 diabetes across three immune effector cell types. Nat Commun. 7,13555(2016)

## 相关阅读

- [放疗治疗也能让喉癌患者病情稳定](https://github.com/l9lvqnbe4d/pregnancy-diary-hub/blob/main/20260911xcbm/zoaerbrbvn.md)
- [高龄女性难孕多年进行试管医治需要做哪些检查？泰嘉运贴心科普指南！](https://github.com/wggadvmpg6/parenting-daily-tips/blob/main/20260910tgwf/dpcumpabvh.md)
- [精液不液化好不好治(一个卵子两个精子双胎)](https://github.com/s4be62o8zt/mommy-baby-notes/blob/main/20260910skos/zvwdmrcsvz.md)
- [【抗疫专题共三篇】众志成城抗疫情，白衣天使暖青城](https://github.com/yoz4ykilda/maternal-health-hub/blob/main/20260911bniw/hkprshhqlh.md)
- [专业引领促成长 砥砺前行正当时——昆明医科大学第二附属医院建院70周年院庆之“5.12国际护士节”表彰大会成功召开](https://github.com/exfk8bm0mc/kids-nutrition-notes/blob/main/20260911ccnx/idlivtmkht.md)
- [哺乳期堵奶原因大家知道多少？](https://github.com/uyv65mt699/baby-product-notes/blob/main/20260911wwfa/poyxrjteqm.md)
- [海南试管婴儿做完多少钱一次？海南试管婴儿辅助中心？](https://github.com/l5q2j5iic2/mommy-baby-notes/blob/main/20260910qvqw/mtmkiywzka.md)
- [儿子切除左侧附睾婚后还能生育吗？](https://github.com/cfo5j5htmg/pregnancy-nutrition-notes/blob/main/20260911jmbv/jegmpabuej.md)
- [胎盘早剥多久胎儿缺氧](https://github.com/a66uv6rprt/newborn-parenting-log/blob/main/20260911jobi/dxrxtgokxv.md)
- [试管婴儿流程揭秘，哪家医院做专业？](https://github.com/tp7gz3q4gt/child-care-essays/blob/main/20260910bqay/avgsqvagsy.md)
- [单身可以做试管婴儿吗 多少钱啊](https://github.com/ovix8rnv9x/parenting-daily-tips/blob/main/20260910rtks/jqmfxlvuev.md)
- [杭州试管婴儿生龙凤胎的费用！选对助孕医院价格更优惠](https://github.com/cwz1rtzls4/pregnancy-care-hub/blob/main/20260910osqy/oeygdcqtqo.md)
- [邯郸不孕不育医院流程,有成功案例吗？](https://github.com/i90i293865/family-baby-log/blob/main/20260911fxig/vxbbvxexyd.md)

## 推荐站点

- [['https://www.fyluanpu.cn/127654991272.html', '厦门试管婴儿哪家好？公立VS私立，成功率最高的医院深度测评']](https://www.fyluanpu.cn/127654991272.html)
- [['https://www.cd-hssf.com/310041272106.html', '孕妈必知周期表算法🈷️,试管代孕流程与费用，国内供卵哪里有']](https://www.cd-hssf.com/310041272106.html)
- [['https://www.anyhdlyb.cn/2859916290671.html', '山西哪个医院做佛山代生试管婴儿成功率高？']](https://www.anyhdlyb.cn/2859916290671.html)
- [['https://www.hg00fj88.com/2099.html', '胚胎移植后会不会掉出来胚胎移植后什么情况会掉出来']](https://www.hg00fj88.com/2099.html)
- [['https://www.szanguangkeji.cn/tongxingshiguanzhuyun/94.html', '三代试管能否实现双胞胎？风险与考量']](https://www.szanguangkeji.cn/tongxingshiguanzhuyun/94.html)
- [['https://www.apkbwvg.cn/danshenshiguanfangan/145.html', '输卵管积水对试管婴儿着床的影响与治疗对策']](https://www.apkbwvg.cn/danshenshiguanfangan/145.html)
- [['https://www.vhpowpj.cn/20250821-153.html', '供卵试管婴儿取卵后，如何促进卵巢快速恢复？']](https://www.vhpowpj.cn/20250821-153.html)
- [['https://www.hghbjm.com/194.html', '江西哪里做试管婴儿成功率高？']](https://www.hghbjm.com/194.html)
- [['https://www.bjwdzxkj.cn/2649220470581.html', '54岁的郭敏做试管是自己的卵还是借的卵子？,做试管代孕要多长时间']](https://www.bjwdzxkj.cn/2649220470581.html)
- [['https://www.lianhuahushengqun.cn/312141998354.html', '福建医大一院生殖中心靠谱吗？资质、技术及挂号攻略']](https://www.lianhuahushengqun.cn/312141998354.html)
- [['https://www.sdxxy.cn/20250604-490.html', '济南做三代试管最好的私人医院分别是哪几家？']](https://www.sdxxy.cn/20250604-490.html)
- [['https://www.mymydz.cn/115974283359.html', '徐州十大试管婴儿医院流程，选择正规助孕机构的技巧,正规的代孕公司']](https://www.mymydz.cn/115974283359.html)
- [['https://www.cddyunw.com/126615031223.html', '上海备孕技巧：排卵日同房如何提高生男孩几率？']](https://www.cddyunw.com/126615031223.html)
- [['https://www.gaodunxinkj.cn/20250518-172.html', '单身去乌克兰代孕, 孕35周尿蛋白3个+且血压经常处于临界值要终止妊']](https://www.gaodunxinkj.cn/20250518-172.html)
- [['https://www.chdhaishendq.cn/212932873315.html', None]](https://www.chdhaishendq.cn/212932873315.html)
- [['https://www.cheguangfu.cn/245.html', '试管婴儿代孕哪个医院好,苹果数据网络打开了连不上网怎么回事（数据网络打']](https://www.cheguangfu.cn/245.html)
- [['https://www.sjzgwfjwzhs.cn/11546127448886.html', '周口代生价格费用多少私立医院有哪些？周口哪家医院做代生价格费用多少成功率高']](https://www.sjzgwfjwzhs.cn/11546127448886.html)
- [['https://www.liangzimayi.com/110.html', '武汉康健医院供卵排队多久？教你一招快速配对不用等']](https://www.liangzimayi.com/110.html)
- [['https://www.dgshengxigongchengsl.cn/3772973102002.html', '华西附二院做供精代生孩子中介成功率高吗？附详细成功率情况']](https://www.dgshengxigongchengsl.cn/3772973102002.html)
- [['https://www.ewdboe.cn/129180326425.html', '北京备孕造人营养补充指南：关键营养品解析']](https://www.ewdboe.cn/129180326425.html)
- [['https://www.hflrwzhs.cn/171.html', '备孕必做！郑州各大妇产医院卵泡监测套餐价格及便捷程度横评']](https://www.hflrwzhs.cn/171.html)
- [['https://www.bubustuff.com/11.html', '南昌市助孕服务网排名榜：综合实力前五强机构名单']](https://www.bubustuff.com/11.html)

*本文整理自母婴健康资讯，仅供科普参考。*
