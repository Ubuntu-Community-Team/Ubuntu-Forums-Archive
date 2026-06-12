---
title: "Mathematica 7 slow under Ubuntu 10.04 (lucid)"
date: 2010-05-20
forum: Education &amp; Science
---

### Post by konstant@mail.ntua.gr on 2010-05-20
After spending a lot of time trying to resolve how to make Mathematica 7.0 not to consume a lot of CPU resources, I decided to summarize it here, in case people find it helpful. First download the attachments. Then  (assuming the tar.gz files are in your home directory ~/):

> cd /usr/local/Wolfram/Mathematica/7.0/SystemFiles/Libraries/Linux
> sudo mv libML32i3.so 00-libML32i3.so
> sudo tar xvfz ~/libML32i3_for32.so.tar.gz 
> sudo chmod a+rx libML32i3.so
> cd ../Linux-x86-64/
> sudo mv libML32i3.so 00-libML32i3.so; sudo mv libML64i3.so 00-libML64i3.so
> sudo tar xvfz ~/libMLfor64.tar.gz
> sudo chmod a+rx libML*.so

Java still takes ~ 15% CPU time. Open a (separate) notebook and
Needs["JLink`"]
UninstallJava[]

Every time you use java (e.g. in the Help center), java starts again. When you finish and don't wish to spend the 15% CPU time anymore, call 
UninstallJava[]
again (...and again)

Some people find it useful to disable java alltogether:
> cd /usr/local/Wolfram/Mathematica/7.0/SystemFiles/Links/
> sudo mv JLink 00-JLink
Help center is not available in that case (as well as other java stuff). Rename 00-JLink back to JLink and you are back to normal (uh, well...)

References:
[http://ubuntuforums.org/showpost.php?p=7486232&postcount=46](http://ubuntuforums.org/showpost.php?p=7486232&postcount=46)
[http://ubuntuforums.org/archive/index.php/t-1136142.html](http://ubuntuforums.org/archive/index.php/t-1136142.html)
[http://www.linuxtent.com/?p=266](http://www.linuxtent.com/?p=266)
and possibly many more...



-------------------------------------------------------------

I also got the following response from Wolfram:

Hello Konstantinos,

Thank you for the email.

This is a known issue, and we advise the users who get into High CPU usage
to use the following Binary instead.

[http://download.wolfram.com/?key=QNQKNV](http://download.wolfram.com/?key=QNQKNV)
 


Sincerely,

Aravind Hanasoge, Ph.D.
Technical Support
Wolfram Research, Inc.

---

### Post by Garyu on 2010-05-24
Shouldn't it be possible to just have Java on one core and do the math stuff on other cores? Most people have dual- or quad-core processors nowadays but afaik Mathematica only uses one core by default...

---

### Post by adeelajaib on 2010-06-03
Thanks Konstant :)

---

### Post by evencoil on 2010-06-03
The java enabling/disabling seems like kind of a pain (at least for someone like me who needs to consult mathematica help constantly).

Is the performance increase from just changing the libraries significant?

---

### Post by lucasp0927 on 2010-06-09
Nice tutorial, thank you!

---

### Post by matyi!dog? on 2010-06-09
This fix worked great on my Dell xpsM1330 . 
Now Mathematica 7 consumes only 2.3% CPU when not computing. 
On clicking Help, Java kicks in and consumes 15% from then on.
Following the kill Java solution does remove Java until the next click on Help. 

Thanks for the effort to solve the CPU problem with Math 7 on Ubuntu 10.04.
I have resisted upgrading to 10.04 until this was solved
since I use Mathematica every day for my number/plotting crunching.

---

### Post by ursula1 on 2010-06-20
Konstantinos, you're my hero.  System monitor now reads 0% CPU usage between calculations for  "Mathematica" and "Mathematica Kernel".  Both were formerly 12%.  

-dal
thinkpad X201t, Intel i7-620LM, 3GB ram

---

### Post by cmumford on 2010-07-10
I had the same problem when I was evaluating Mathematica prior to purchase. I followed your steps above and it did indeed reduce my CPU utilization - I think to maybe 6% or so.

However, I just purchased Mathematica, and decided to use their support to get an official fix. They sent me what I believe is a prerelease if 7.0.2 and the problem is now completely fixed. I can even bring up help and close it without any unnecessary CPU usage.

Ahhh - silent computer once again.

---

### Post by alexalexalex on 2010-07-25
I installed the file the Mathematica guys sent you.
Ah, my computer finally stopped squeaking!!!
Thank you so much!

---

### Post by dikdirk on 2010-08-13
Thnx, solution worked for me!

---

### Post by Cloud_704 on 2010-08-29
[COLOR="DimGray"]I'm a noob, what do I do with that .sh file downloaded from wolfram?[/COLOR]

Edit: never mind ... have to put "sh" in front of the file name

---

### Post by el_jee on 2010-09-09
Does anyone have a mirror for the script?

Unfortunately it is not available anymore on the Wolfram server.

---

### Post by ccordoba12 on 2010-09-10
Thank you very much Konstantinos for publishing the fix to this issue.

I couldn't use Mathematica for over a year because it took like 40% of my CPU (and I have a quite laptop). Now it consumes like 6-8% but because Java is on.

---

### Post by joerenes on 2010-10-23
The fix also works for me in 10.10 (maverick). Thanks!

---

### Post by the_luke on 2010-10-29
the file is no longer online at wolfram. i have 7.0.1 and experience problems starting (even with the suggestions from the first post). firing up the gui takes ages.

---

### Post by pitibu on 2010-11-19
Thanks a lot Konstantinos.. it worked for me.
Also, the links to the files in wolfram seem not to work anymore, so thanks a lot for attached them.

By the way, I am using mathematica 7.1 and had the same problem (now solved).

---

### Post by De Baimbo on 2011-02-05
You really saved me. I'm using Mathematica 7.0.1 on a 9-year-old laptop without any problem thanks to your solution. \\:D/

---

### Post by jpxsat on 2011-04-28
Same here, on a ten years old pc!!
Mi mhz are safe with this patch!! A great solution for low spec computers are surely an increase of performance for new hardware as well.:P

---

