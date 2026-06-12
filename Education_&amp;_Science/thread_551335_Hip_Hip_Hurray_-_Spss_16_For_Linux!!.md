---
title: "Hip Hip Hurray - Spss 16 For Linux!!"
date: 2007-09-15
forum: Education &amp; Science
---

### Post by fsando on 2007-09-15
It is now confirmed - SPSS 16 WILL run on linux - only Exact procedures will still be windows only!!!
From PR blurb:

"Improved flexibility with a new Java interface
Portability and Extensibility with Mac OS X and Linux versions of SPSS desktops and non-English versions for SPSS for Mac and Linux
Support for Unicode"

---

### Post by machoo02 on 2007-09-15
Save yourself several hundred dollars....use R instead.

---

### Post by fsando on 2007-10-12
> **machoo02 said:**
> Save yourself several hundred dollars....use R instead.

I'm already a long time user of R - and very pleased at that and Rkward is also a  great interface. 
But what this really means is that universities and research institutions the world over will have one less obstacle to using linux.
I believe it is very important that one of the most used statistical packages is now coming to linux.
This is for statisticians much like what a linux version of Photoshop would be for people working with graphics.

---

### Post by bojo42 on 2007-11-13
... and with version 16 you can use R within SPSS! That's really cool, so the SPSS fans can try R now very easy and so this may led to an very soft switch towards the "free world" :guitar:

---

### Post by giannis1_86 on 2007-12-19
'R' is good.....but is it possible free spss download? even 14 or 15 version...

---

### Post by fsando on 2007-12-20
Unfortunately we are still waiting for spss for linux here in europa due to a "period/comma" bug.

---

### Post by Radon on 2008-01-07
I got to try out the SPSS 14 student version on my laptop yesterday.  From the command line, wine gets stuck at the "What would you like to do" box and crashes with a whole page of details of errors.  So close, yet so far...

I'll see what I can do tomorrow.

---

### Post by ecmarvellous on 2008-09-15
pls, can R do regression? and if I can get some free versions of spss, how do I do that? pls, help. I have a work I started with spss but my pc crashed I need to redo some regression work I did to enable me complete the work. need ur help.

---

### Post by earlycj5 on 2008-09-16
> **ecmarvellous said:**
> pls, can R do regression? and if I can get some free versions of spss, how do I do that? pls, help. I have a work I started with spss but my pc crashed I need to redo some regression work I did to enable me complete the work. need ur help.

R does much more that just simple regression.

But here's something I had a hand in writing on linear regression in R.  Non-linear is also in this document.  [http://199.86.26.56/education/AdvancedPlantPath/Topics/RModules/Doc1/04_Linear_regression.html](http://199.86.26.56/education/AdvancedPlantPath/Topics/RModules/Doc1/04_Linear_regression.html)

---

### Post by gunksta on 2008-09-16
Hip Hip Hurray - PSPP works on Linux too!

What the heck is PSPP?

PSPP is a project, by the FSF, to implement a SPSS clone liensed under the GPL. I like SPSS but I like PSPP even better even though it's not complete yet. The latest version, 0.6, version is a real improvement.

Do NOT use the version hiding in the repos unless you have upgraded to 8.10 already. The version of PSPP in Hardy, 0.4.3, is not worth messing with. I may write up a FAQ on the PSPP website for compiling on Ubuntu, but with the latest version included in 8.10, it doesn't seem like the best use of my time.

The best part about PSPP is that it uses SPSS syntax. I have no interest in getting into a flame-baiting contest about the merits of SPSS syntax v. R. Both are excellent tools, with different strengths and weaknesses. PSPP's compatibility with SPSS makes it easier for me to work collaboratively with the other analysts in the office who use SPSS. Being able to share my syntax with them (and vice-versa) is important for little details like quality control and re-use of code. R can be used to read and write the data tables, but the syntax is completely incompatible.

If you like SPSS and would prefer to use an open-source tool, I encourage you to give PSPP a try. Get involved and help it become THE statistical tool for Linux.

[PSPP]("http://www.gnu.org/software/pspp/")

---

### Post by earlycj5 on 2008-09-18
> **gunksta said:**
> Hip Hip Hurray - PSPP works on Linux too!

What the heck is PSPP?

PSPP is a project, by the FSF, to implement a SPSS clone liensed under the GPL. I like SPSS but I like PSPP even better even though it's not complete yet. The latest version, 0.6, version is a real improvement.

Do NOT use the version hiding in the repos unless you have upgraded to 8.10 already. The version of PSPP in Hardy, 0.4.3, is not worth messing with. I may write up a FAQ on the PSPP website for compiling on Ubuntu, but with the latest version included in 8.10, it doesn't seem like the best use of my time.

The best part about PSPP is that it uses SPSS syntax. I have no interest in getting into a flame-baiting contest about the merits of SPSS syntax v. R. Both are excellent tools, with different strengths and weaknesses. PSPP's compatibility with SPSS makes it easier for me to work collaboratively with the other analysts in the office who use SPSS. Being able to share my syntax with them (and vice-versa) is important for little details like quality control and re-use of code. R can be used to read and write the data tables, but the syntax is completely incompatible.

If you like SPSS and would prefer to use an open-source tool, I encourage you to give PSPP a try. Get involved and help it become THE statistical tool for Linux.

[PSPP]("http://www.gnu.org/software/pspp/")

Looks interesting.  I'm too heavily invested in R at this point to consider picking this up as a serious tool but I'll definitely install it for interest's sake.

---

### Post by gunksta on 2008-09-18
Here's my 10 cents. If you are already using R, and are happy with it, I would stick with it. R can actually do MORE than PSPP can, and that will undoubtedly stay true for the forseeable future.

If you already know SPSS, and like it, or need to use SPSS syntax . . . . . PSPP offers you a realistic route to using open-source applications rather than proprietary tools.

At first blush the two tools seem very similar, and in many ways they are, but they really do have different end users in mind. Because of the way SPSS/PSPP handle missing data and such, it is often easier to use for Social Sciences research, where missing data is a just a way of life. R is going to be better at some things.

PSPP brings more choice to the ecosystem AND provides new linux users with a tool that will be very similar to the one they may have used in the Windows world . . . while R tends to be rather foreign to people who have never programmed in an Object Oriented language.

---

### Post by earlycj5 on 2008-09-19
> **gunksta said:**
> 

PSPP brings more choice to the ecosystem AND provides new linux users with a tool that will be very similar to the one they may have used in the Windows world . . . while R tends to be rather foreign to people who have never programmed in an Object Oriented language.

That would be one reason I'm interested in knowing something about it myself.  People ask me about stuff like this and I hesitate to recommend R to everyone.  This seems like it could be useful in some situations to other people.

---

### Post by astarr on 2008-12-30
> **gunksta said:**
> PSPP brings more choice to the ecosystem AND provides new linux users with a tool that will be very similar to the one they may have used in the Windows world . . . while R tends to be rather foreign to people who have never programmed in an Object Oriented language.

i'm new to linux, and i just got it working for ubuntu 8.10. found this thread through a google search and it helps. thanks everyone!

---

