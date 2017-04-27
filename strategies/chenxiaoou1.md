本文为汇眼见识会第一期（3月26日）的纪要
嘉宾：知乎上的ID“用Python的交易员”
转载请联系汇眼微信号Huiyankefu授权
导读：量化交易的概念在近两年越来越热，量化与外汇的结合也是最近外汇交易者和爱好者们探索的话题，汇眼有幸请到了知乎上的量化交易专家陈晓优老师为大家解惑如何用量化的方式做外汇交易。
用Python的交易员——金融工程学硕士，毕业于伦敦卡斯商学院，拥有多年私募基金和量化投资从业经验，日常工作中每天负责期权波动率套利、CTA、价差套利等量化策略的实盘交易和研发，目前参与管理的产品规模在数亿级别。开发维护了一款针对国内市场的开源量化交易平台开发框架vn.py，目前是国内用户最多的量化金融开源项目之一（Github Star 1341），业内目前有几十家私募公司在实盘使用。
我们在此先安利一下嘉宾的历次知乎Live与知乎专栏：用python的交易员 - 知乎
感谢大家参与今天的见识会，今天的主要内容是从量化的角度做外汇交易，我本人是从外汇交易起步入门才会选择了走金融这条路，本来大学的志愿是化学，但是因为交易引发了兴趣才转成了金融，硕士选择了金融工程方向并且在英国工作了一段时间，可以说我的金融之路是从外汇和MT4开始的。
确实在过去的十年中，外汇行业迎来了翻天覆地的发展，但是也注意到现在国内外汇的交易员还是主要在采用主观、手工的交易方式，或者相对比较简单的MT4上的EA交易，我今天首先给大家介绍在国际市场上比较主流的量化交易方法的分类。

在这张PPT里面，我把外汇领域的策略大体分为三类，分别是量化宏观、CTA、高频交易三类，这也是是对策略的具体持仓周期的区分，量化宏观对应的是超长期或者长期、CTA对应的中期或者短期，高频交易对应的短期或者超短期。
第一种类型就是量化宏观，如果大家对对冲基金行业有所了解呢会知道基金业有一种大类的策略叫做全球宏观（Global Macro），这种策略主要是通过对全球经济宏观面的预测，从上至下的方式来筛选并进行外汇、期货、股票等标的的交易实现该策略的交易目标。
比较知名的全球宏观策略使用者就包括索罗斯、保罗杜伊琼斯，这两位就是主流的主观的全球宏观策略基金的领头人了。
全球宏观这种策略是对某一个国家或者某一个领域的未来一段时间的预测，除了人的主观判断之外，还可以用量化的模型把基本面的数据、价格面数据、历史数据、分析师预测加在一起来产生一种信号比较强的中长期的预测。
在这一块的比较有代表性的公司的包括SLJ Macro Partners，在伦敦哈罗兹百货的对面，过去几年的表现非常好，已经成长成了全球范围上著名的以外汇为主要投资资产的一个量化宏观策略对冲基金。
除此以外还有一个更有名的，但是现在已经不行了的对冲基金——FX Concept，历史有30多年，当年跟桥水不分上下。但是因为2008年后全球央行因为次贷危机不断干预市场，量化宽松，导致他们原来的量化宏观策略不适应新的市场环境了，华尔街见闻曾经做过他们的专题报道，我把链接给大家放出来：
全球最大外汇对冲基金FX Concepts的兴衰史（上） - 华尔街见闻
全球最大外汇对冲基金FX Concepts的兴衰史（下） - 华尔街见闻
大家有兴趣可以自己了解一下，这一类外汇量化宏观策略可以分为两类：一种叫做定向交易，简答而言就是做方向，比如我们认为美国经济会好，那么我们就买一些美元或者美元指数；另一种叫做相对价值交易策略，比如我们认为美元强、欧元弱，那么我们进行一些欧美货币对的配比，还有类似货币对原油、货币对黄金这样的一些价差对比。
量化宏观领域的模型更多是涉及经济与基本面的数据，当然也会结合市场的行情数据，全球市场上的价格本质上是基本面的经济数据驱动的，尽管会有一些情绪、资金流、技术面造成的市场噪音与波动，但是长期而言是向着基本面给出的方向去走的，所以量化宏观的策略给出的信号非常的强。
同时因为这些模型的信号周期比较长，预测一年内的信号都算短的，长达三四年的预测都是常见的。在这个策略的交易过程中，可能交易的重点都不在于信号本身了，而是在于基于信号方向建立交易持仓量的控制，市场交易中对于自己不利价格的风险控制，这个时候就要一些水平比较高的对冲策略与短线交易了，比如进行一些外汇期权交易、价差交易。
第二类策略就是外汇CTA策略，这一类的代表一家叫Winton，一家叫做Man AHL，这两家公司有很深的渊源，20年前Winton的创始人之前是Man AHL公司的CTA部门的负责人，20年之后这两家公司都已经成为了世界上顶尖的CTA类的基金。
CTA这个策略比较偏中期或者中短期，基于技术信号、市场特征进行一些中短期的投机。因为这个CTA策略是基于价格的，所以所有有价格的资产都是可以使用这个策略的，包括外汇期货、股指期货、股票等标的CTA基金都有可能去做，覆盖面比较广。
CTA的策略一般持仓周期比较短，有一些策略甚至是日内平仓的（Day Trade），对于交易的价差（Bid Ask）比较敏感，所以这两家CTA对冲基金都和最大的经纪商（Tier 1）或者银行进行交易，比如高盛、JP Morgan等等，几亿或者几十亿的交易规模可以拿到比较低的执行点差。
补充一个量化宏观策略的细节，量化宏观策略的信号强、频率低，一年内出现的交易机会是比较少的，所以宏观量化策略的交易者对于交易成本不是很敏感，电话交易下单比较常见，对于经纪商的价差不是很在意，更在意的交易的量（流动性能有多少）；但是CTA对于执行时间与成本的要求就高了。
最后一类就是国内传的神乎其神的高频量化交易了，国际上高频量化交易确实有一定的技术上的要求，但是原理上也没有那么复杂。最具有代表性的就是花旗银行、德意志银行的外汇量化部门了。
投行的代表有Morgan Stanly、高盛、BNP、法兴银行等等，自营交易商的代表是Citadel，KCG等等；Citadel城堡基金分成两个部门，一个是自营、做市部门Citadel Security，一个是资产管理部门 Citadel AssetManagement，这两个部门是完全不同的：外汇做市的部门是Citadel Security，Citadel Asset Management会采用一些宏观量化、CTA的策略来进行外汇交易。
高频交易这类的外汇交易策略主要是高频做市，基于时间序列模型和市场微观结构的量化交易策略。其实就是基于时间序列模型和市场微观结构的历史数据进行统计，解析市场价格在未来数秒内的走势，加一个价差并且提供报价，赚取点差。
客户与高频做市商交易，做市商赚到点差，如果市场变动慢那么做市商的敞口风险也比较低；市场变动比较快的时候，高频做市商可能会选择在银行间市场把自己的敞口对冲出去，赚取银行间市场与下游市场之间点差的差值利润。
所以高频交易就要求低延时的交易系统，最少到微秒级甚至纳秒级的交易速度。所以大家平时听到有些高频交易公司跨州、跨洋拉光纤，甚至买军方退役的微波塔，一般都是用来进行外汇方面的高频交易的。
主要原因就是因为外汇领域的交易所（ECN）非常多，跨市场套利的机会很多，所以外汇高频交易就是要速度快。
还有高频交易这块做市商是报两个价格（Bid Ask），大家平时看到的欧美货币对的点差归根朔源就是来自于当时银行间某一个做市商的做市报价。

讲完了策略，我们来将一些跟我们比较接近一些的量化交易平台的介绍。
国内对于这一块的接触不是很多，最常见的就是MT4\MT5，还有一些交易商提供一种新型的平台Ctrader/也叫作cAlgo，这家交易平台做的也很不错。
还有一个我稍后会介绍的Multi Charts，这是一个美国的老牌、有很多客户基础的量化交易软件，不仅仅适用于外汇，还能交易股票、期货、期权等等，有很多的机构用户与对冲基金在使用这个平台。
后面我还会介绍两个机构级别的平台，一个是Algo Trader，还有一个是我本人开发的VN.PY，门槛比较高，对于用户的编程能力与交易能力都有一定的要求，我们还是先从简单的平台开始介绍：
首先MT4/5是最常见的，国内做外汇的客户都见过这个平台，在一开始的时候外汇经纪商的平台都是自己研发的，后来的几年里俄罗斯的MT4/5击败了这些成为了行业的一种标准化的解决方案。
这个软件是免费的，在量化方面的开发环境是MQL4/MQL5分别是基于C语言与C++语言的，在这两个环境里开发量化策略只能实现基于Tick与Bar的驱动策略；Tick是指交易商的每一次报价，Bar是K线的运行。
但是无论是比如我挂了一个单，现在成交了；或者之前挂了一个委托，发了挂单撤销，撤销成功等这一类的信号，在MQL环境中都是没有办法监听的，只有在下一个Tick/Bar发来的时候去请求查询自己的委托、成交情况。
这就造成了MT4/5是不可能实现高级的交易策略的，无论是CTA策略还是高频策略都是无法实现的，这是架构上的问题。我对MT4/5的定位是对于入门、爱好者的适用软件。
第二个平台是CAlgo，这也是一个免费的平台，提供的编程环境是基于C Sharp（C#）的，这是微软开发的，在业内编程语言功能最强大的开发环境之一。
在架构上，CAlgo是允许Tick驱动、Bar驱动，除此之外还有成交驱动，比如你下了一个交易委托，委托的结果会马上被监测到，可以让你的策略被再次调用，所以CAlgo是可以用来实现一些低延时的CTA类的交易策略的。我对CAlgo的定位是一个常规的量化适用环境，可以实现业界一些比较常见的策略与交易。
第三个就是有十年历史的Multi Charts，前身是Trade Station的开发团队（将近30年历史），这一个老牌、经典的软件是1500美金的终生使用价格，但是每年会有更新，每次更新还有升级的费用。
Multi Charts的开发语言有两个，一个是Easy Language，一个是C#。C#在上文已经阐述过了，而Easy Language被誉为量化交易业内的奇迹，可以让开发者用近似于英语的语言来描述自己的交易逻辑。
所以这个语言是非常非常的容易，兼顾了扩展性与复杂应用可能性；同时支持Tick驱动，Bar驱动，支持上文提到的成交驱动，还多了一个委托状态变化的驱动，这就使得一些复杂架构的订单，比如FAK、FOK，还有一些特殊的算法订单，所以符合一些成熟的量化交易者去使用，而且因为语言非常友善，极易上手。
Multi Chats在全球范围内都有机构客户、基金公司客户在使用，整体而言这家软件公司的东西很好用，公司效益也很不错。
提到机构用户，我要提到之前在网上看到，一些外汇交易商推广的时候说自己的MT4很多对冲基金都在用、银行间都有使用，以我个人的认知而言这是很扯的，的确银行的外汇零售部门提供MT4给自己的客户使用，但是机构与银行的内部的自营部门（Prop Trading Department）是肯定不会用的，这个是产品架构造成的缺陷。

说完了之前三个常规一点的平台，现在来介绍两个适合大型量化外汇机构使用的量化交易平台，一个是AlgoTrader，一个是我本人开发的vn.py。和之前三个平台不同的是，之前三个平台虽然能做，但是还是停留在支持基于价格变动、单交易品种的策略，不能支持复杂数据结构。对于大型量化交易机构，几个亿、几十个亿的策略产品需要不是仅仅简单基于价格的平台。
首先说AlgoTrader，是一个瑞士的公司开发的一套量化交易系统，曾经是一个开源项目，因为非常成功所以成立了一家公司提供量化对冲基金业界对于产品有高性能、高要求的客户。基础价格是2000美金一个月，而且根据需求提供不同的插件和模块（另外付费），全套产品要几万美金一个月的价格。
AlgoTrader的编程语言是Java，同时AlgoTrader内置了一个复杂事件处理引擎CEP，通过这个技术（开源的叫做Aspera），在商业化开发之后（商业收费版叫做Aspera Advanced）可以达到纳秒级内进行复杂事件的处理。
这一块平台更适合专业的交易机构交易员，可以实现复杂的量化交易策略，比如跨货币对期权的波动率交易策略，我们也成为离差交易（Dispersion Trading），这是一种可以支持大资金量去进行交易的一种策略。
第二个VN.PY是开源的，也是免费提供大家去使用的，源代码可以在GITHUB上下载和开发，这是一个基于近两年比较火热的Python语言的产品。VN.PY没有使用这些成熟的商业化事件处理引擎，我自己设计了一个轻量级的事件引擎。
同时VN.PY相比起AlgoTrader把所有的引擎包含在自己的框架里面不同的是，我们采用了模块化的设计，比如独立的风控引擎、CTA策略引擎、外汇交易引擎、期权交易引擎、套利引擎等等，把这些引擎以扩展模块的方式插入到主程序去使用，更适合一些定制化的策略，比如期权的做市，期权与货币对波动率相关的交易等等。
VP.PY也有比较高的入门门槛，首先需要熟悉Python语言的编程，也需要明确知道自己的交易系统具体是怎么实现的，所以现在VN.PY的用户都是资深量化交易用户，目前都是国内的私募、券商自营、海外的采用复杂策略的对冲基金在使用。
平台这块讲完了，但是只有平台没有经纪商还是没法做交易的，所以我们接下来讲一讲那些经纪商适合去做量化交易。

摆在第一位的就是盈透证券（Interactive Brokers），支持美股、外汇、期权、期货、甚至一些OTC市场的债券都可以通过一个账户交易，他们的平台TWS是我见过的最强大的交易软件之一，比高盛、大摩提供的软件强大的多，虽然这些银行可以交易更多的品种，但是大多数是要通过电话交易的，但是盈透把这些交易都兼容在了自己的平台里面。
同时盈透的API接口（IB API）也是全球、业界用户最多的之一，外汇市场的部分，盈透建立了一个ECN平台，其实是采用了交易所的模式，是一种叫做MTF的模式，但是盈透因为没有交易所牌照只是叫自己ECN。
简单而言就是做市商在市场上进行了报价，如果有客户想要在你报出的价格成交，即使做市商的价格已经发生了变动，但是在这个市场上变动还没有发生，做市商是不能拒绝以原来的价格跟客户成交交易的。
但是对于很多的外汇市场ECN平台，比如FXALL、CurrenX都是做市商只在ECN平台上报出一个做市意向价格，成交请求递交给做市商后，做市商有权拒绝在该价格成交交易（Last Look机制），此时ECN平台只能把客户的单子再提交给第二好价格的做市商，这就可能导致客户的单子在市场之间游荡但是得不到执行。
最后的成交价格可能与你的下单价格偏离很远了（滑点），这是普通的纯ECN的平台的缺点，但是IB的IB PRO平台采用的MTF平台就能保证客户的下单价格的成交。在欧美很多体量小于一亿美金的基金都会选择与盈透进行交易，节约了自己开发清算系统的成本。当然体量大的基金公司还是会选择与大银行比如高盛、花旗去做交易的。
IB自身是没有提供量化交易平台的，TWS（Trade Work Station）本身很强大，IB API也是通过TWS实现的，但是并没有自动化量化交易策略的支持。很多公司开发了特别的接口去支持IB的API接口，比如上述提到的Algo Trader，VN.PY等等。
第二家比较合适的公司是Oanda，从加拿大起家的公司后面把总部搬到了美国，他们在业内很特别，其实是一家外汇服务商，业务分为三条线，第一个部分是现汇兑换（Deliverable FX ）业务，一个比银行的成本低的兑汇业务；第二个部分是为跨国企业提供外汇对冲的咨询服务，提供定价策略等等；最后一个部分才是OANDA的外汇交易部分，就是外汇杠杆保证金交易业务。
Oanda也是一个业内技术革新比较积极的公司，他们提供了自己的Web Rest API，基于HTTP协议的，几乎所有的支持HTTP发起的编程语言都支持他们的API，但是性能上有所牺牲。
第二块，他们有自己性能比较好的JAVA接口，还有FIX接口，这是大型金融机构的解决方案。OANDA是纯做市商模式，也已自己是一个做市商公司为自豪，信誉也很好。
在国际上有很多跨国公司是使用Oanda的兑汇服务的，比如Airbnb，在Airbnb的不同国家的显示的房价外汇价格与换汇价格的服务提供方都是Oanda。
同样Oanda也没有提供任何的量化交易平台，提供API的服务。

还有三家公司我们接着介绍，Dukascopy中文名叫杜高斯贝银行，LMAX交易所，以及本次活动的赞助商ICM CAPITAL，我们先介绍持有瑞士银行牌照的杜高斯贝。
Dukascopy提供了一个自己开发的量化交易平台叫做JForex，还有一个自主的外汇量化交易环境，提供量化策略历史回测等功能，还有一个比较鸡肋的可视化外汇策略编辑器。
听起来很神奇，但是我本人认为这更多是一个玩具，这种可视化策略开发的功能是一个期货领域的顶尖的公司TT/X_Trader的开发商（Trading Technologies）集合了几百个工程师花了几年的时间开发出来的，但是Dukascopy的产品就简单很多了。
我看过Dukascopy的FIX API文档，其FIX协议设计是远远超过FIX普通协议的，对于机构客户有很大的吸引力，他们也是ECN的平台，业界的声誉（欧美外汇交易圈子）也不错。
第四家外汇经纪商，更多的应该说他们类似外汇交易所的机构，也就是LMAX。他们拿的是英国正规的MTF牌照，类似于美国的Dark Pool暗池的场外交易所。他们跟IB的IB Pro一样用的是MTF模式，上文已经介绍过了，所以受到了很多对冲基金的青睐，同时他们下设了两个其他业务。
第一块是他们的MTF类交易所业务，也是管的最严的，第二块是他们的银行间接入服务，也是比较正规。LMAX第三块，也就是国内接触最多的，但是面对散户的LMAX Professional，这一块相对没有那么正规，跟其他普通外汇经纪商类似了，但是这不说他们其他两块LMAX Inter Bank与LMAX Prime不够好，后面两者在英国还是有很多大型金融机构使用的。
同时LMAX可以说是技术驱动上最强的公司之一，如果写过JAVA、关注前沿技术的朋友们应该听说过Lock-Free Queue（汇眼：快速无锁队列），LMAX发明了Java上的非常强大的功能，在GitHub上的得分非常高，高频交易机构的应用非常多；同时他们还发明了一个Distributor模型，这是一个把交易订单以路由的方式发送，实现一旦数据流出现问题，可以用固定算法把整个交易状态重现的一个非常好的核心交易系统，LMAX的把这两个组建都开源了。
然后LMAX Professional，也就是面对散户的业务的程序化借口也挺多的，有C#，JAVA和FIX，但是他们的门槛比较高，我当时想把VN.PY去接，但是门槛跟盈透差不多了。LMAX提供MT4与MC（上文提到的MultiCharts）。
最后需要强调一点，LMAX在国内有大量的代理商，而且在国内是很混乱的，代理商加点（加手续费）可能很多。我觉得你如果很懂的话可以直接联系LMAX，不要通过LMAX的国内代理商来做。
最后一个就是ICM CAPITAL，是一家FCA持牌的英国经纪商，他们量化方面提供一个叫做ICM DIRECT专业客户服务体系，包括FIX API借口，为专业机构提供服务，内容有托管，融资等方面的服务。
经纪商这一块讲完了，我来分享一下我参与外汇的量化的过去经历，是时间比较久远、学生时代的故事，先说在IG，现在叫Digital 100，当年叫IG Index的做二元期权的经历。

大家应该都听说过二元期权是什么，也即是Binary Option，也叫作Digital Option，二元期权是一种盈利或全亏（asset or nothing）期权，交易者投入一定的金额博弈市场的价格，可以看多也可以看空，如果在约定期间后的市场价格符合交易者的判断，交易者可以得到70%-85%（取决于二元期权交易商或者期权合约内容）的收益；如果不符合交易者的判断，那么交易者将会亏损85%-100%。本质上是一个赔率1赔不到1的一个游戏，但是特点是时间非常短，可以赌一天、五个小时、甚至一个小时之后的情况。
IG这家公司在二元期权领域的一个先行者，在英国学术圈最早的几篇跟二元期权有关的论文都是跟IG有关。另外他们是第一个推出叫Customer Bet的服务，让客户自己选择期权的行权价、行权时间、行权条件的服务，具体可以看上面的这个图。
二元期权也分成欧式与美式两种，欧式二元期权在行权期到之前行权价格是没有意义的，行权到期时候的价格才决定客户是赌赢还是赌输；美式二元期权则是只要价格在行权期内碰到了行权价，那么客户就赌赢了。
欧式二元期权，这种期权比较难以定价，如果大家学过期权定价理论大家是可以提出解析解的，也就是用计算机是可以快速定价的；而美式二元期权（One Touch）是没有办法算出解析解的，只能用蒙特卡洛模型去算出近似解，IG当时二元期权定价模型是不完善的也有很多问题，只是用了数学上叫做近似法的方式提进行较简陋的定价，给我们带来了套利的机会。
为什么要用模特卡罗呢？这是因为未来的行情是很难预测的，我们只能根据概率、未来回报率和回报率波动来假设，模拟出不同的路径，然后把这些路径算上自己的路径概率和收益情况，再得到自己的预测价格，就算用计算机去跑这种数学预测方法也是非常慢的。IG只能用近似法去定价，这种方法是有很大缺陷的，我们交易者就可以建立一个叫做conditional volatility pricing module的模型。
也就是条件波动率定价模型，其实没那么复杂，就是在特定情况下市场的潜在波动率我们是可以预测的，如果我们知道未来的波动空间是多少，我们就能通过报价测算出收益大概是多少，我们在当时做到了二元期权上的稳赚。
是什么情况下呢？就是经济事件公布的时候，非农、Fed会议、GDP数据公布的时候等等，市场的波动率可能是多少是可以通过历史数据来进行统计的。这个现象叫做Volatility clustering（波动率集簇现象），距离来说就是统计一下过去一年非农数据公布后美日货币对的波动范围是多少，比如是70个pips，我们再反过来看IG给出来的赔率是多少。
如果IG给我的赔率对我来说是有吸引力的，比如70个pips的波动基于模特卡罗预测法的概率是非常低的，IG给我70pips波动情况下一赔二、一赔三的赔率，我们用条件波动率定价模型知道在非农数据中70个pips的波动是有80%的可能性的，那么我们就能算出自己的预期收益率（80%可能性一赔二、一赔三，20%可能性亏损），这个情况下我们就可以满仓去搞了。
我写了一个两个月200镑到30000镑的故事，是我的同学做到的，我自己交易是风险控制很重，每次只用不到5%的仓位，所以自己只盈利了大概2000镑。
赚了很多之后IG发现了这个漏洞就把我同学的账户给封了，然后IG改进了自己的定价模型，起码在非农之前把自己的定价策略改了，消除了这样一个套利机会，整个交易机会前后也就四个多月的时间，其实金融市场还是很有效的，这样的无风险套利机会很少见，出现也会很快被大家消灭掉。
第二个经历是我个人的经验，用EXCEL做自动化交易。对IB熟悉的话知道他们有两个API可以用来用EXCEL实现的量化交易，一个是EXCEL VBA，一个是EXCEL COM接口，通过EXCEL来实现自动下单、自动撤单这样比较简答的策略，这是我大学有基金工作经验的授课教授传授给我的。

所以我就结合VBA API自己写了一个EXCEL，通过多张Sheet做了一个数据结构，跑起来之后用实盘做了一段时间，赚了一点小钱，发现这个赚钱的效率比IG的套利赚的少多了，我当时以为对冲基金赚钱都跟IG套利一样所以就觉得EXCEL赚钱太慢了，但是现在有了基金的工作经验之后才知道IG套利跟路上见到金子的概率一样，可能一辈子也就那么一次机会。这个EXCEL来做量化交易的经历是我第一次接触量化，起码写了一个程序、用了EXCEL把程序跑起来了，还有了实际交易盈利的经验。
分享这段经历也是想告诉大家，对量化感兴趣的话不用觉得入门的时候有多困难，就选一些你能做的事情，找到了方法和方向，日积硅步，不要上来就学Deep Learning这种让你都不知道自己在干嘛的东西，每天都有进步过个几年你总能有自己的累积和成就。
最后跟大家分享的就是当时做社交交易的事情，这个也是我不是很喜欢MT4 MT5的原因。

当年社区交易就很火，一般都是MT4/5软件的，简单来说就是跟单啦，当时有mirror trading，Zulu trade等等，在这些社区上投顾（晒单的人）给出一个买卖信号，通过社区交易平台把这个买卖信号传给订阅者，我的账户在根据这个信号去进行交易。
听上去好像还可以，本质上就是你雇佣了一个投顾，他来帮你操盘，有点类似基金经理抽一个成，但是其实跟基金完全不一样，这是一个不靠谱的东西。
很多看上去资金曲线特别漂亮的，大多采用了一种叫做Martingale（马丁格尔）的策略，其实就是亏损了不止损，死扛，选择一个价位翻倍加仓，如果价格回到入场位就相当于把之前的亏损都赢了回来还有盈利，但是如果翻倍加仓之后价格继续走不利于你的方向，那么你的亏损就特别厉害了。
很多这种社交交易社区给你看到的资金曲线，并没有包含投顾在持仓期内的资金曲线，看不到持仓期中的最大回撤，而是只给你看平仓后的资金曲线，所以你看到这些投顾都在赚钱，但是其实完全不是这样。这些投顾只是在赌自己运气好，不会爆仓而已（也就是在赌自己不会碰到Tail Risk）。
但是实际上呢，如果大家接触期权的话就知道期权有一个波动率无效的情况，原因就是实际金融市场上的回报率肥尾现象（暴涨、暴跌的概率）是远远大于正态分布给出的预测的，所以马丁格尔这样的策略可能90%的交易都是赚钱，但是如果碰到一次肥尾现象就直接爆仓了。
第二个问题就是延迟，投顾下单的信号给了社交交易社区，社交交易社区给我，我再把单子交给自己的经纪商，这中间多个环节可能造成了几秒甚至几十秒的延时，造成了一个非常大的滑点，这是我当时血的教训，我跟了一个排名第一的投顾，交易的结果是很惊人的，短短两个月我跟的投顾涨了15%，我自己亏损了30%，每天都在稳定亏损，自己意识到这个有很大的问题。
我自己分析发现，这个投顾用的就是马丁格尔策略，然后延时又造成了我下单跟投顾下单点位的巨大滑点。这个延时造成我下单的单子成了给他下单的单子在“抬轿子”，他下单我在下单价格就打上去，他离场我再离场价格就又被打下去了。所以跟单的人越多，抬轿子的人越多，而跟单的人亏得也就越多。
然后还有一些无良的公司，直接在后台改曲线，把亏钱的曲线改成了赚钱的，当然这个现象在股票和期货里面也有。我个人是不太推崇社交交易的，如果这个人做交易真的那么厉害，为什么不自己做私募基金发产品呢？
最后还有用MT4开发策略的经验，虽然MT4有优化参数功能，但是优化的时候只支持穷举的模式，可能会导致过度拟合，也就是你的策略曲线很漂亮，但是在实盘里面是没有意义的，只是历史数据曲线漂亮而已，会导致你误判自己的策略的胜率。所以我的定义是MT4用来做量化只是适合爱好者玩玩而已。
讲座的内容就到这里了，接下来是问答环节：
提问： 现在市场上有许多外汇公司，有的白标，有的贴标，真假难辨？给的条件一个比一个优惠，说实话汇市做成像国内大宗。所以老师怎么辨别以及业务发展趋势？
回答： 这里我比较推荐大家关注汇眼，帮助交易者在交易商筛选上做了很多的工作和努力的，他们筛选出来的结果总比你一家一家乱敲门好，你可以以汇眼给出的公司作为起点自己再选择，如果汇眼都没有给出推荐的话那就没有什么好考虑的了。还有你可以参考一些大的公司在海外是怎么经营业务的，因为其实合规的交易商给出来的条件不会太丰厚，如果给你条件太好的公司那么很可能是有一定问题的。
提问： 外汇交易各个市场在纯技术分析下的有效性是否一致？有时候发现技术分析咋特定的时间段特别有效，有时候失效，一般会是什么原因造成的？
回答： 这个问题的话，其实是怎么界定你的分析有效，如果你的预测方法有问题，给不出任何信号那么就没有太多意义了。其实技术分析这个东西市面上大多的东西都是错的，或者无效的，真正有用的东西还是在一个小圈子里面流传着。
这么说，你可以统计一下你用某个方法预测市场的正确率，如果都是五五开的话，那么你选择的这个方法很可能就是毫无价值的。
提问： MT5这个平台从下单到成交的过程是怎么样的？成交速度和其他平台比较如何？
回答： 对于所有的外汇交易商来说，基本上都是一样的，你看到的MT5都是在你电脑上的客户端，你的订单发送给了我们称为“撮合系统”的一个东西，做市商会判断你这个订单是否能够执行，ECN平台会把你的订单路由给平台上价格最好的一个做市商。
所以你问成交速度MT5与其他平台的比较是没有太大意义的，因为就算是同样用MT5的经纪商不一样，背后的成交机制不一样，交易的结果会是千差万别。在这里还是推荐一下汇眼的测评，他们的报告中有涵盖这一块，写的还是不错的。
提问： 外汇平台的ticks数据是如何收集的？是每成交一次就生成一个实时推送一个吗？
回答： 外汇市场的tick呢，据我所知，绝大部分不是按照成交推送的，而是基于每一次报价的更新推送的（quote），如果报价商每次更新了一次数据那么tick就更新了一次，所以外汇市场显示出来的交易量是没有太大意义的，每个交易商的量都不同，除非你自己在花旗银行你知道银行的量是多少，这个量才是真实的。
提问： 量化策略正是上线之后，是如何管理策略的？另外策略一上线就面临drawdown，老师如何处理心态？
回答： 策略的管理，最重要的是你看每天运行的实盘跟回测是否一样，实盘的运行每天你要做回测，如果回测的结果跟实盘是一样的，那么就没问题，但是如果不一样没那么就要修正你的策略了。
策略上来就面临drawdown，其实只要你的策略开发的方法是靠谱的，一系列测试都是通过的，不是通过数据拟合的方式造出来的结果，交易系统是有逻辑性的，那么就算上来有draw down也没关系，除非你的模型本来就有问题，这就是另一回事了。
提问： 外汇市场的level 2数据有用吗？假设要写个日内超短scalping策略，需要花时间研究吗？比如Dukascopy的，好像只有limit单数据却没有成交数据
回答： 对于Dukascopy而言的话，我认为他们的level 2数据是没有意义的，因为这个数据是他们ECN平台上的数据，而真正有意义的数据掌握在Tier 1 Bank上，比如德银的外汇部门，Dukascopy的这个数据样本太少，并没有参考的价值。
提问： 用Matlab开发外汇交易策略或做历史数据回测是否可行？
回答： 是可行的，但是开发的策略本质还是取决于你的能力和水平。
提问： 目前大陆大多在用马丁或网格加仓。你们有好的算法交易策略没？
回答： 我可以讲几个策略的，比如有期权的波动率交易，期权离差交易，Low Latency交易，HTF Cross Market Arbitrage & Market making，这些Google上都可以搜到资料。这些东西可以直接说，因为这些策略背后的涉及的技术和东西非常的复杂，没办法用简单的MT4来做。社交交易的话，机构里面做量化交易员自己也有个小圈子，大家聊到过这个东西，比如把自己的策略卖出去到社交交易平台上，但是这种模式研究下来的效果是不可行的，效率很可能低于对冲基金自己的盈利率，所以是不可持续的。
最后附上一张图帮大家解析一下AHL公司的业务：

Man Group主要是做CTA方面的策略的，AHL Alpha是Trend Following；AHL Currency多策略可能有Trend-Following，可能有Relative Stress，可能有Carry Trade；AHL Evolution除了Trend-Following之外，还有交易很多小国家的货币，AHL是这些交易的专家。
还有AHL TRAGET RISK，说是balanced Long Only，也就是个多头策略，用比较复杂的量化模型获得更好的风险收益比，但是市场的风险是没法控制的，这个Beta Risk是次贷危机后十年对冲基金跑不过ETF的主要原因，所以AHL推出了这样一个策略目标是跑赢大盘。
还有AHL Volatility，TailProtect，这些刚刚都提到过，是波动率交易和保护肥尾现象风险的产品。