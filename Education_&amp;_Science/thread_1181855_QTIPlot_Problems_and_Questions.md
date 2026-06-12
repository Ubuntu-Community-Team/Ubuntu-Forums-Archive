---
title: "QTIPlot: Problems and Questions"
date: 2009-06-08
forum: Education &amp; Science
---

### Post by superdan006 on 2009-06-08
Hello,

I'm running Hardy and am becoming frustrated working with QTIPlot 0.9.3. This was the version I found on synaptics.

It behaves fairly inconsistently: crashing when minimizing graphs, inconsistent line fitting, etc. I am using qtiplot as a linear regression tool for data columns I've pasted from an OpenOffice.org spreadsheet. 

I have a few questions:
1) Has anyone else encountered similar problems using qtiplot in Ubuntu 8.04, etc.

2) From its website, I downloaded the linux package for qtiplot 0.9.7.6. I untarred it and am unsure what to do next. Can anyone instruct me how to build qtiplot? 

3) Does anyone feel that building it would be worth it. Is another software available that has a simple enough user interface to import spreadsheet columns, plot a selection of those columns, and then fit ALL the data linearly and collect the regression data (residual value, equation of line, etc.)

Thanks,
-dan

---

### Post by spinoza666 on 2009-06-14
> **superdan006 said:**
> Hello,

I'm running Hardy and am becoming frustrated working with QTIPlot 0.9.3. This was the version I found on synaptics.

It behaves fairly inconsistently: crashing when minimizing graphs, inconsistent line fitting, etc. I am using qtiplot as a linear regression tool for data columns I've pasted from an OpenOffice.org spreadsheet. 

I have a few questions:
1) Has anyone else encountered similar problems using qtiplot in Ubuntu 8.04, etc.

2) From its website, I downloaded the linux package for qtiplot 0.9.7.6. I untarred it and am unsure what to do next. Can anyone instruct me how to build qtiplot? 

3) Does anyone feel that building it would be worth it. Is another software available that has a simple enough user interface to import spreadsheet columns, plot a selection of those columns, and then fit ALL the data linearly and collect the regression data (residual value, equation of line, etc.)

Thanks,
-dan

Hey Dan,

1) I've installed qtiplot successfully on 8.04 and now Jaunty, without any of the stability issues you mention from the repos. I don't know why you are experiencing these problems, but why not try to reinstall and see how it goes?

2)If you follow this tutorial on how to install from source, you should have a functioning qtiplot in no time at all:

[http://www.tuxfiles.org/linuxhelp/softinstall.html](http://www.tuxfiles.org/linuxhelp/softinstall.html)

3) I am also looking for some good open-source/free plotting software, and qtiplot is the best I've come up with so far that has a graphical user interface, and is easy to use. For other options check this link out:

[https://help.ubuntu.com/community/UbuntuScience](https://help.ubuntu.com/community/UbuntuScience)

If you are doing a lot of stats I would recommend R, which is availabe in the repos as r-base and r-base-dev, and to check this site out for further installation queries:

[http://lib.stat.cmu.edu/R/CRAN/](http://lib.stat.cmu.edu/R/CRAN/)

R is quite heavy duty, but once you learn it, you will never go back. I am looking software that I can use in conjunction with R, that will allow me to easily produce publication quality graphs working in an graphical environment, and have so far come up with qtiplot, which I frankly find quite lacking. R produces beautiful graphs, but I prefer to work graphically when producing graphs, and in commandline when doing analysis. Give me a shout if you find something good:)

---

### Post by venik212 on 2009-07-07
The idea of an ORIGIN clone is great, but there are so many things wrong with this program that it is almost pointless to list them.  Here is a short partial list:
--When I try to view the worksheet, the program crashes
--When I open a saved project, the column headers are replaced with 0s, so the graphs are all wrong.
--Layer arrangement does not work correctly-- removing the space between layers does not really work
......
I am using the latest (0.9.6.7) under Kubuntu 9.04 (KDE 4) on an HP 64 bit machine.
I would love to see this thing work, but so far it is very far from Prime Time.

---

### Post by veli on 2009-07-07
I agree with Venik212. I've tried the program a couple of times, but it is so buggy, and seems there are fundamental mathematical mistakes in its code. Linear fitting on logarithmic plots for example doesn't work correctly, actually it does not fit the data correctly. There were also some other annoyances (ASCII data import AFAIR), these issues were discussed on the users forum, without a solution I think so far. If you need just a plotting program, stick with Open office Calc, and for statistics get something else.

---

### Post by venik212 on 2009-07-08
I second the recommendation for R for statistics, and also for some decent graphics.

---

