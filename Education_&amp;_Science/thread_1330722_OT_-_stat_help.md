---
title: "OT - stat help"
date: 2009-11-18
forum: Education &amp; Science
---

### Post by memilanuk on 2009-11-18
Hello,

I was wondering if anyone here knew of a forum, mailing list or newsgroup that would be considered somewhat 'newbie friendly' for people needing some help with statistic modeling?  My primary intent is to use R, but their mailing list seems more oriented towards debugging R solutions i.e. the assumption is that you already know what the correct model is for a particular application.  I've taken a Stat 140 class (generic intro to statistics course), but some of the things I'm interested in now are just a wee bit beyond what was covered in that class in any depth.

Thanks,

Monte

---

### Post by gunksta on 2009-11-18
I dig your avatar. Someday I'm going to find a more amusing one.

Regarding your question - I'm sure there are some stats oriented mailing lists out there somewhere, but I'm not sure where.  Have you looked at Google Groups? Your assessment of the R mailing list is basically dead-on. There are a few modeling related discussions, but these usually start when someone disagrees with someone else's approach, based on the OP. It's an R list, not a stats list.

That being said, there are a few people on there that I wish I could ask specific stats questions too because I'd love to hear their answers.

Oh well.

Surprisingly, there are a few of us on this list who like statistics. Throw out your question. Most (all?) of the stats folks here like/prefer R, so it's likely that our ideas will be easy to translate to your problem.

---

### Post by memilanuk on 2009-11-19
I had looked at sci.math, sci.stat.edu and sci.math.stat a few times... guess I got kind of turned off by the rampant spamming that is on most newsgroups these days.  Kind of a catch-22... I don't have a dedicated usenet account anymore (getting a little hard to find as part of a regular ISP account these days), so I can't filter the groups through an off-line reader such as Thunderbird or slrn, with a kill-file to plonk the loonies in :rolleyes:  Google Groups has some nifty search features, but so far I haven't figured out how to filter the results to keep all the nasty stuff at bay.

So... what I want to do is measure and test a component used in a hobby of mine.  The goal is to determine which measurements that can be taken at the end-user level bear the strongest relationship to the end parameter, velocity(MV).  The basic measurements consist of 1) weight before prep (W1), 2) weight after prep (W2), 3) volume before initial use (V1) and 4) volume after initial use (components are commonly utilized from 5-10 times subsequent to the initial use).  I'm currently debating whether to go for a second velocity (MV2) measurement to explore the relationship between velocities obtained with virgin components vs. fire-formed components.

Some of the obstacles I need to deal with:  At least one of the measurements is somewhat tricky to do consistently, at least with the tools available to me.  I need to determine how much error/inconsistency is present and include it in the analysis.  Another problem is the test instrument used for measuring the final parameter (MV) is one of those that getting any concrete numbers out of the manufacturer regarding % error is like getting blood out of the proverbial turnip... and its basically not possible for the end user to do their own testing to determine it.  Furthermore... the test that generates the final parameter (MV) is essentially a one-time event - it is not possible to repeat that same event with exactly the same pieces, as most of them (with the exception of the component I have been measuring) are consumed in the process.

So, assuming I've soldiered on through all the above, and have recorded data points for W1, W2, V1, V2 & MV, including some form of % error for each kind of measurement.  This is the point at which I start going... now what?

I did a simpler version of this for the final paper in my Stat140 class... essentially W1, V1, & MV.  Didn't cover std error at all (the one thing I got dinged on), and found out the hard way that while W1 and MV showed a mediocre, but statistically significant relationship... M1 and V1 did not, and V1 and MV did not either.  There are some concrete reasons as to *why* which do make sense... but I want to 'see' if the values obtained from W2 or V2 show a more strongly significant relationship, or if some combination thereof does.

The stat class I took covered simple linear regression a bit, mentioned std error in passing (which was why I forgot about it when doing my paper), pretty much skipped error bars, determining the % uncertainty, etc.  ANOVA was pretty much just mentioned, but not covered, and multiple regression not at all.  I've got one book on [error analysis]("http://www.amazon.com/Introduction-Error-Analysis-Uncertainties-Measurements/dp/0935702423/ref=sr_1_1?ie=UTF8&s=books&qid=1258610089&sr=1-1") that looks like it should be of value in this endeavor.  Another book that I have covers multiple linear regression and regression model selection in light detail - mainly because it is oriented towards teaching a non-statistician how to plug-n-chug the numbers in Mini-Tab.  As a result, I don't have a good feel for how I'd do the same in R, and most requests for guidance end with a recommended reading list consisting of expensive 20-30yr old texts that require more understanding of calculus and/or linear algebra than I currently have.

Any ideas, suggestions, or comments would be very welcome.

Monte

---

### Post by andrew.46 on 2009-11-19
Hi memilanuk,

> **memilanuk said:**
> I had looked at sci.math, sci.stat.edu and sci.math.stat a few times... guess I got kind of turned off by the rampant spamming that is on most newsgroups these days.  Kind of a catch-22... I don't have a dedicated usenet account anymore (getting a little hard to find as part of a regular ISP account these days), so I can't filter the groups through an off-line reader such as Thunderbird or slrn, with a kill-file to plonk the loonies in :rolleyes: 

If you were keen to return to Usenet your best bet is to have a look at individual.net which only costs €10 per year and has superb filtering. I have been with them for 2 years now and spam is almost non-existent.

All the best,

Andrew

---

### Post by memilanuk on 2009-11-19
Andrew,

Thanks for the suggestion... unfortunately most of those groups have been pretty much destroyed by the spammers.  Not much left *but* the spam any more.

Thanks,

Monte

---

### Post by spinoza666 on 2009-11-19
Why don't you just get a good R book. It seems to me that what you are trying to do requires quite basic analysis, and both of these books cover that nicely, and more:

[http://eu.wiley.com/WileyCDA/WileyTitle/productCd-0470510242.html](http://eu.wiley.com/WileyCDA/WileyTitle/productCd-0470510242.html)

[http://eu.wiley.com/WileyCDA/WileyTitle/productCd-0470022981.html](http://eu.wiley.com/WileyCDA/WileyTitle/productCd-0470022981.html)

Have a read through the modelling bits, and I'm sure you'll come up with a solution. You should note that these books are very much how-to, and not so much why you're doing what you're doing. But they cover this in a basic sense as well.

---

### Post by spinoza666 on 2009-11-19
Oh, and some advice for the analysis is in place

Assuming I've understood your problem correctly.

Arrange you're data properly, i.e. weight is one variable, before/after is one variable, and so on. Do some basic linear modelling (lme or glm in R perhaps?), check the fit of the model, have a look at the intercept and slope effect of all the your variables, plus standard deviation to check the significance. This is a quick and dirty way of estimating the effect of each variable on the response variable. 

But please note, there are several pitfalls and this might not be the correct method for you, so you should read up on how to do this, and get some in depth explanation.

---

### Post by NikoC on 2009-11-19
This one often helps me on my way: [http://www.rseek.org/]("http://www.rseek.org/")

---

### Post by gunksta on 2009-11-19
Below, you will find a bunch of links. It sounds like you've got an interesting question to answer and I think this gives you enough to do some reading and figure it out. I would read up on manova and multiple linear regression.

But before you get into building a complex model, I would wonder about a few things that a mathematical model can't understand, but could affect your outcome. From reading your description, it sounds like MV is going to be your dependent variable. Assuming that this object (model rocket?) is moving in the real world and not a research facility, there are many things that could affect the real-world MV, which could be why the manufacturers are unwilling to release some of this information. It could be misleading.

**Disclaimer** **-** I haven't take physics in a long time and I don't actually know what you are launching, I'm just thinking extemporaneously.

And, if MV is your dependent variable, I don't understand how you intend to measure the affect of your independent variables on the dependent variable if you aren't measuring this for yourself (I understand that measuring this may be difficult/impossible). In most experimental designs, you change x (weight) and see how it affects y (velocity). While I think your model probably works (x1,x2,x3 affect y1) I don't know if using numbers from the manufacturer, that are obtained outside of the influence of your independent variables is going to be very useful, unless they are also providing the information regarding the independent variables, in which case I'll just shut up.

Again, I could be way off base here, but it doesn't sound (to me) like you have a direct reason to conclude that changes in your model will affect the outcome.

One final note - I'm not sure what you meant by new virgin v. fire-formed components, but if you think it's an important factor, I would recommend gathering data on the variable. In this case, I would create a variable nuses which records the number of times a component has been used (0,1,2,3,4,5). This is going to be a factor variable.

Collecting this data into your data set seems to be trivial (compared to the other data sources) and could be important. Fact is - if you don't gather the data, you will never know. When you get to the analysis stage, you can look at how it affects things. If it doesn't appear to be important, drop it. If it does appear important, keep it.

------------------------ Links ----------------------------------------

There are many on-line sources for learning about statistics. Here are a couple:

[http://statsoft.com/textbook/stathome.html](http://statsoft.com/textbook/stathome.html)

[http://faculty.chass.ncsu.edu/garson/PA765/statnote.htm](http://faculty.chass.ncsu.edu/garson/PA765/statnote.htm)

Personally, I tend to like the latter one, but I think it's just because of the way my brain works and because I do applied social research unfortunately, you are asking a physics question. You might google for the MIT Open Courseware site. There might be some resources there that would be better suited for understanding how to apply statistical methods to physics experiments.

I haven't looked at usenet in years and it is really too bad that spammers have managed to kill so many good mailing lists and open forums. We even see spam in this sub-forum from time to time. The moderators do a good job killing it off, but it does sneak in periodically.

Of course, there is still the minor issue of actually completing your analysis in R. (Computer make everything so complicated.) Learning how to search about R is critical:

[http://www.r-project.org/search.html](http://www.r-project.org/search.html)
[http://www.rseek.org/](http://www.rseek.org/)

And let's face it, R is a bit confusing at times:

"An Introduction to R" is a good place to start:
[http://cran.r-project.org/manuals.html](http://cran.r-project.org/manuals.html)

And here's something I wish I'd found earlier:
[http://wiki.r-project.org/rwiki/doku.php](http://wiki.r-project.org/rwiki/doku.php)

And there is a really nice site here (Link is to the sitemap):
[http://www.statmethods.net/about/sitemap.html](http://www.statmethods.net/about/sitemap.html)

The guy who wrote this last page is also writing a book and the draft is available on-line (there's a link on his page). I haven't looked at this yet, but if it's as good as the on-line stuff he has developed (assumptions get me in trouble sometimes) it's going to be a good book. It may also be useful to you, but I don't know.

---

### Post by memilanuk on 2009-11-19
Actually... I do have a few books on R, as well as a lot of megabytes worth of R tutorials.  Figuring how to do basic stuff in R isn't the problem - or at least if I hit a stumbling block, I know where to look, or where to ask.  I don't think any of those books go into much detail on MLR, or model selection.  The few that do unfortunately go over my head rather quickly.  There are a few new books (2009-2010) specifically on 'modern regression' techniques in R that I may look at.

As for the specific application... I was kind of dancing around it because some people get a little weird about the general topic.  In particular, the 'components' are brass rifle cases as used in handloading for long-range competition.  

I'm looking at comparing the initial weight out of the bag (W1) vs. weight after case prep which removes minute amounts of material from key areas (W2) vs. internal capacity as measured by plugging the flash hole and filling with H2O, weighing before and after (V1) for 'virgin' brass, and then again after firing ('fire-formed').  There may be a degree of correlation between not just the final velocity MV (muzzle velocity) and individual predictors, but between them, which I believe is termed 'multi-collinearity'? E.G. the heavier a particular case is, the more metal present and the less volume ultimately available for expansion of powder gasses during combustion... except not *all* of the places that thicker brass may occur would directly affect that volume - i.e. case head, extraction groove, etc.  

There are a number of other issues that also affect muzzle velocity which need addressed... fouling the bore of the barrel before hand so I don't have some rounds riding on bare metal and some not, getting the barrel up to a stable temperature but controlling the rate of fire to not let it get too hot... precisely weighing the powder charge on a lab grade scale to maintain consistency... sorting the bullets by various factors (including bearing surface) to make sure they are as consistent as possible and do not add any more variables to the final measured muzzle velocity.  Some items, like primers, are fixed and there isn't much I can do about them - can't alter them, not really sure of what can be done in terms of measuring that is worthwhile  that can be done.

The final parameter, MV, is measured by a chronograph, which basically has two optical sensors that pick up, literally, the shadow of the bullet as it crosses over the instrument and computes the velocity based on the time lag between one end and the other.  Getting the % error for this instrument out of the vendor is what I meant was difficult.  It may well be that the level of accuracy available at this point may render the rest of the experiment moot if it cannot record the values with enough precision to be able to draw a clear conclusion.  Which reminds me... I need to sit down at some point and do some power calculations as far as what I really need for sample size.  Unfortunately, real-world budget and the consumable aspect of most of the components (bullet, powder, primer, and to a lesser extent, barrel and brass) put some limits on how big of a sample I really can use.

Monte

---

### Post by gunksta on 2009-11-19
Very interesting. I don't know why I didn't think of that given what you said. (I should drink more coffee in the morning before hitting the forums.) Now that you've explained everything, my concern regarding MV was clearly misplaced.

You're right. There are many things that could affect MV. And I suspect you are right, multicollinearity may be a concern but given what you are trying to do, it should be a rather small concern, as long as you only use your model to predict the total outcome, MV.

Like I said earlier, I do most of my work with people and, surprise, there are plenty of variables that impact outcomes that we can't measure or the measurement of that variable is less precise than desired.

I agree. You should try to work with the manufacturer to get the error range of the device. On the other hand, you are trying to understand a relationship and you could argue that if you do lots and lots of round - then the error should be essentially random and shouldn't totally foul up your test. But, this obviously adds cost to the equation.

Last week I went to a presentation on the use of dependent sampling. The presenter discussed the usual caveats in doing social oriented applied research and then concluded that an approximate answer is often we are ever going to get, but that is better than nothing. I think the same could apply here too.

You have clearly thought about some of the things that could affect your outcome measurement and you are going to take steps to minimize the affect of these as best you can. Don't sweat the small stuff.

Regarding power - it might be easier to simply pick a number of rounds that you are willing to / can afford to fire and then calculate the power from there. If it's acceptable, you have yourself a design. If not, save a little more money.  :-)

I don't reload (I'm lazy that way) but I suspect that high quality bullets are going to be more or less similar. You could test your chronograph by taking it to the range and firing a box of store-bough shells (get good ones). Assuming you keep the gun clean (don't forget about heat - that definitely affects things over time) and other factors the same, you should be able to get a good sense of how consistent your results are. It would also be a good way to play around with a few other gun-related factors and what not to work out your process before using your hand-made rounds in the experiment. You can work out the kinks in your testing methodology with rounds which should be more or less consistent (I'm assuming this is true, you know more than I do in this regard) but it could be a comparison group if nothing else.

It's an interesting questions and I'm curious to see how it all comes out.

---

