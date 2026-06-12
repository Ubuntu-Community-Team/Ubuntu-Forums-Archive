---
title: "R commander:the model AnovaModel1.1 is no longer available"
date: 2010-10-02
forum: Education &amp; Science
---

### Post by demandeinfos on 2010-10-02
Hi,

When I do an ANOVA with R Commander, this message appears : "the model AnovaModel1.1 is no longer available".

Please, could you give me an advice for this ?

Thanks

---

### Post by gunksta on 2010-10-02
That's interesting. I don't usually use Rcmdr, unless I want a fast and dirty way to look at the data (because R lacks a good way to view data frames otherwise).

So, I loaded up Rcmdr and tried to run an ANOVA. And, it worked just fine. But, I did look at the syntax that Rcmdr is using and I _think_ I know what is going on.

Rcmdr creates a variable called AnovaModel#. It keeps track of how many tests you have done and increments the name each time. Since you are missing AnovaModel1.1, it looks like you are doing a multi-way ANOVA and for some reason the first time (.1) R uses the aov command (which would create AnovaModel1.1) something is crapping out and the variable is never formed. Rcmdr doesn't give you the results directly. Instead it uses summary() to display the results of aov(), which is a perfectly good approach. But, if aov() doesn't complete for some reason, you'll get the error you are seeing.

Why is aov() not working -- I have not idea. I would probably start by looking for data quality issues. The error you are reporting isn't the juicy one. To be of more use, I need the the data set you are attempting to use OR the error aov() is throwing when Rcmdr attempts to create that model. Otherwise, I can't really help much more.

If you look at the data and you aren't sure what's going on, feel free to PM me with the data. You don't necessarily need to upload here for everyone on the planet.

---

### Post by gunksta on 2010-10-02
Small correction. Model1.1 is just the first model. I thought it might have something to do with the type of ANOVA you were using but I don't think it does.

Otherwise, I think my last post is more or less accurate.

---

### Post by demandeinfos on 2010-10-03
Thanks a lot for your answer. I think you mean that it is likely due to a wrong choice for the test (could be not used with my data ?).

I give you here the table I used. Please, could you tell me if it corresponds to an 2 factors Anova ?

Read you soon ... ;)

AAA, BBB, CCC .... measured parameters
X, the 2 factors : a and b


X;AAA;BBB;CCC;DDD;EEE;FFF;GGG 
a;1;5;4;1;1;5;5 
a;2;6;1;2;2;4;4 
a;1;4;2;4;5;8;8 
a;2;2;5;5;4;9;7 
a;3;1;4;6;1;8;4 
b;4;3;2;5;2;7;5 
b;5;5;1;4;2;4;4 
b;1;4;3;1;5;5;5 
b;2;1;6;2;1;8;4 
b;3;2;5;3;1;7;5

---

### Post by gunksta on 2010-10-03
That certainly helps. Your data looks fine. (Although it helps if you write it into the window in a way that makes it easy for someone to load it into R for themselves.) In this case, I don't see any odd-ball values (like an errant "C" in a numbers column or any missing values.

But, multi-factor anova can not, to the best of my knowledge, be done through the Rcmdr interface. Rcmdr uses the aov() command, which is different from the anova() command. 

I really shouldn't try to answer forum posts late on Saturday night. My brain is not operating in an optimal manner.

Rcmdr can do simpler anova (or the equivalent) through aov(). I still don't understand the error you are getting until I can see what aov() is struggling with.

---

### Post by demandeinfos on 2010-10-03
Thanks one more time for your answer.

Shall I summerize what you wrote by this : it is better to use aov() command from R console than using R commander ?

I ask you this, because I 'm not sure that R commander is interesting. Indeed, I have also problem with PCA. When I do a PCA no graph appears ...

Wish you nice sunday  :)




ps : "Although it helps if you write it into the window in a way that makes it easy for someone to load it into R for themselves." : I don't no know how to do in another manner ... ;)

---

### Post by gunksta on 2010-10-03
Depending on your perspective -- the fact that R does not really have a comprehensive GUI is either a problem or the #1 reason to use it.

Are you familiar with PSPP or SOFA Statistics? If you are looking for a stats package with a real GUI interface, these might be better options for you.

[http://www.gnu.org/software/pspp/](http://www.gnu.org/software/pspp/)
[http://www.sofastatistics.com/home.php](http://www.sofastatistics.com/home.php)

PSPP is in the repos. Sofa is not, but if you are using Lucid or Maverick, you can use the new version and install it via a single downloadable .deb file. Just download the file and then open it with gdebi. Install.

--andy

---

### Post by gunksta on 2010-10-03
> **demandeinfos said:**
> I don't no know how to do in another manner ... ;)




No worries. There are two options. For a small data set like the one you  showed here, you could provide the code to create the data  frame/matrix. Something like:

```
 xx <- c(1,2,3,4,5) 
yy <- c(5,4,3,2,1)
data <- data.frame(xx, yy)

```

Obviously, this approach becomes problematic with larger data sets. In those cases you could just attach the data as a .csv file or even attach the R environment file stored on your computer.

I think it is fair to say that most (although not all) linux-based R users prefer text-editor interfaces. ESS is a nice interface for EMACS users and another guy on this forum develops a really nice plugin for Vim. Other options to look at would include [JGR]("http://www.rforge.net/JGR/") and [Statet]("http://www.walware.de/goto/statet"). I should look at JGR some more. I have been using a lot of Java programs lately and if I'm going to have the JVM running anywho, I should consider taking advantage of JGR. JGR is a stand-alone system while Statet is an Eclipse extension. I haven't used it much, but it seems like a nice interface. Unfortunately, installing Eclipse requires an enormous amount of hard-drive space that is largely wasted unless you are planning on developing in Java. I don't mind the hard-drive space but you also have to keep all those libraries and systems up-to-date and what not and it just seems like a bunch of cruft.

As to the use of anova() versus aov(), it really depends on what you are trying to do. The beautiful thing about R is that there are often multiple ways to skin the same cat. Unfortunately, that same complexity makes developing a sane, general-purpose GUI nearly impossible.

---

### Post by demandeinfos on 2010-10-15
Hello,

Thanks o lot for your interesting answer.

"I** think it is fair to say that most (although not all) linux-based R users prefer text-editor interfaces.**" 
That's the "problem" for me. I'm not used programs with text-editor interface (and I don't know how to do with that, I'm not informatician). So, I wonder if anyway I would like to find a free statistical software on Linux.

"**As to the use of anova() versus aov(), it really depends on what you are trying to do. **T**he beautiful thing about R is that there are often multiple ways to skin the same cat"**
In few sentences please, could you give me more informations about this, and 1 or 2 examples ?

Thanks again and read you soon :)

---

### Post by gunksta on 2010-10-22
Sorry for the long pause.

If you would prefer something with a GUI -- I would tend to recommend either [PSPP]("http://www.gnu.org/software/pspp/") or [SOFA Statistics]("http://www.sofastatistics.com/home.php"). 

Are you trying to do a one-way or two-way ANOVA? It looks like the GUI only supports a one-way ANOVA although it may be possible to get a two way out of it if you write in the syntax by hand (but that gets us back to something more R-like). SOFA is a little quirky at first, but I think it would be really slick once you get used to it.

Added bonus for SOFA - Because it stores everything in a SQLite database, it's easy to use a central data-set for both SOFA and R. It's a little harder to do that with PSPP because of the inherent limitations in how SPSS/PSPP store the data.

SOFA is programmed in Python, which you previously expressed some interest in, which is another nice detail.

anova() and aov() are nearly the same thing. IIRC, aov() requires you to create the linear model. ?anova and ?aov would give you more info.

---

### Post by demandeinfos on 2011-01-08
Good evening,

Following my last messages I'm now able to make Anova and pair comparisons with R console or Rcmdr. Thanks for your help.

Lastly I tried to do a TukeyHSD test with R concole and it's ok.

I give you the R script :
[B]library(agricolae)
library(lattice)
library(FactoMineR)
a<-read.table("C:/Program...TukeyR2.txt", header=TRUE)
attach(a)
bartlett.test(sol~ph, data=a)
b<-aov(sol~ph, data=a)
summary(b)
c<-HSD.test(a$sol, a$ph, 205, 0.000411, group=TRUE)
[I][U]bar.group(c, main="main title", cex.lab=0.5, cex.axis=0.5, las=1, ylab="pH", xlab="solubilité", col.lab="green", horiz=TRUE, density=4, col="blue",border="red", xlim=c(0,1))

[/U][/I][/B]Yet, I have a problem to modify the graphe and my question is related to the modifications of a graphe using the "bar.group" function. With the script you can see, I can modify the size of the police of the x axis but I'm not able to modify the police of the y axis and the letters on the front of the bars (a, b, bc, bcd ...).

Please, could you help me quickly I need to give a report asap.

Best regards

---

### Post by gunksta on 2011-01-10
Hopefully someone else will chime in. My experience with the lattice package is very limited.  Stack Overflow might be a good resource. The folks there tend to use ggplot2 more than lattice, but I'm sure there are some dedicated lattice users over there.

---

### Post by euler_fan on 2011-01-11
[Bar Chart Man Page for R]("http://stat.ethz.ch/R-manual/R-patched/library/graphics/html/barplot.html")

Is this what you are trying to do? I didn't find a bar.group command in the lattice package. 

Otherwise because you mentioned Tukey's HSD with ANOVA, [Quick-R has some examples of how to do standard things]("http://www.statmethods.net/stats/anova.html").

I am not a huge user of ANOVA personally so I am not completely conversant with what you might be trying to plot.

---

### Post by euler_fan on 2011-01-11
> **demandeinfos said:**
> Good evening,

Following my last messages I'm now able to make Anova and pair comparisons with R console or Rcmdr. Thanks for your help.

Lastly I tried to do a TukeyHSD test with R concole and it's ok.

I give you the R script :
[B]library(agricolae)
library(lattice)
library(FactoMineR)
a<-read.table("C:/Program...TukeyR2.txt", header=TRUE)
attach(a)
bartlett.test(sol~ph, data=a)
b<-aov(sol~ph, data=a)
summary(b)
c<-HSD.test(a$sol, a$ph, 205, 0.000411, group=TRUE)
[I][U]bar.group(c, main="main title", cex.lab=0.5, cex.axis=0.5, las=1, ylab="pH", xlab="solubilité", col.lab="green", horiz=TRUE, density=4, col="blue",border="red", xlim=c(0,1))

[/U][/I][/B]Yet, I have a problem to modify the graphe and my question is related to the modifications of a graphe using the "bar.group" function. With the script you can see, I can modify the size of the police of the x axis but I'm not able to modify the police of the y axis and the letters on the front of the bars (a, b, bc, bcd ...).

Please, could you help me quickly I need to give a report asap.

Best regards

The argument you need for naming the bars is names.arg and I'm not sure what the police of the x or y axis is so I can't help there.

---

### Post by demandeinfos on 2012-04-29
Hi

Since my last message, I'm still not able to use R commander to do one way Anova. I noticed that the main problem is that R chooses automatically Group and Factor, and I can't indicate my own choice (selection is blocked). I tried several options, changing columns and values, but it was impossible to change this automatic choice. Perhaps I will find the solution by chance  ... ;)

Anyway, I try SOFA and I found that it is easily to use it than R commander for Anova. Yet, R commander is great for other treatment as ACP.

Taking into account this, my question is, can I make mean comparison between several groups with SOFA ?

Thanks in advance for your answer.

---

### Post by mdshaver on 2012-04-29
If a GUI interface is desirable for performing your ANOVA, you may also consider several other choices.

QtiPlot [http://soft.proindependent.com/qtiplot.html](http://soft.proindependent.com/qtiplot.html)


Gretl [http://gretl.sourceforge.net/](http://gretl.sourceforge.net/)


LazStats [http://www.statprograms4u.com/LazStatsMain.htm](http://www.statprograms4u.com/LazStatsMain.htm)

Both QtiPlot and Gretl are available in the repos while LazStats is not. The creator of QtiPlot offers fairly low-cost maintenance contracts for those wanting the most recent .debs and technical support. The LazStats website provides generic linux binaries. The menus don't always look right; I think the creator recommended using Fedora but I don't exactly recall. LazStats seems to offer the most options for various ANOVA models.

---

### Post by demandeinfos on 2012-04-29
Thanks a lot for your answer. I will try these solutions.

Yet, If someone can help me to solve my problem with R commander, thanks again.

---

### Post by rewyllys on 2012-04-29
Since R Commander is not providing what you want in the way of a GUI, you might take a look at R Studio to find out what it can do for you, with ANOVA and other statistical operations.

The pertinent URL is:

[http://rstudio.org]("http://rstudio.org")

---

### Post by cellurl on 2012-06-16
[QUOTE=gunksta;9918113]That's interesting. I don't usually use Rcmdr, unless I want a fast and dirty way to look at the data (because R lacks a good way to view data frames otherwise).

Q: If you don't use Rcmdr, what do you use? (I am new to R)

Thanks for any reply!

---

