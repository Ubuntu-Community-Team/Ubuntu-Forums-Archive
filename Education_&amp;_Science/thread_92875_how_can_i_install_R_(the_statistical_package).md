---
title: "how can i install R (the statistical package)"
date: 2005-11-20
forum: Education &amp; Science
---

### Post by albean on 2005-11-20
Hi,

I'm new to ubuntu and linux.  I would like to install R but I don't know how.  I think i have to issue some apt command at the command line, however, I'm not sure exactly what.  I've googled around but could not find anything.  I hope somebody can help me to know what command i should type.

Thanks.

---

### Post by rejser on 2005-11-21
Don't think you can apt-get R.
download  r-base-core_2.2.0.final-0sarge2_i386.deb r-mathlib_2.2.0.final-0sarge2_i386.deb r-base_2.2.0.final-0sarge2_i386.build r-recommended_2.2.0.final-0sarge2_i386.deb (think you need them all, if you run amd64pick the once which ends on amd64) from
[http://cran.r-project.org/bin/linux/debian/sarge/](http://cran.r-project.org/bin/linux/debian/sarge/)
they worked for me.
Normally firefox saves to desktop, so open a terminal and write
cd Desktop && sudo dpkg -i *.deb

---

### Post by rejser on 2005-11-21
By the way, if you have access to spss it runs perfect under wine

---

### Post by Ubuntist on 2005-11-21
I recently installed R using Synaptic -- just do a search for "r-" in package names.

It works fine from the command line -- just type "R" to start.  I've also installed something that is supposed to be a GUI for R, but I haven't yet figured out how to run it.

---

### Post by albean on 2005-11-21
Thanks guys,

I'll give it a try when I get home thise evening.

I'll let you know how it goes.

---

### Post by MakubeX on 2005-12-22
[QUOTE=rejser]By the way, if you have access to spss it runs perfect under wine[/QUOTE]

Perfect? I can't find a way to successfully generate some charts/graphs from my data (when SPSS is executed via Cedega/CrossOver).

In wine, I can't pass the network version/status check - the program terminates a few seconds after showing that "network check" splashscreen.

Do you have some references?

---

### Post by towsonu2003 on 2006-03-03
[QUOTE=rejser]By the way, if you have access to spss it runs perfect under wine[/QUOTE]
spps doesn't wotk for me in wine

---

### Post by towsonu2003 on 2006-03-03
[QUOTE=Ubuntist]I recently installed R using Synaptic -- just do a search for "r-" in package names.

It works fine from the command line -- just type "R" to start.  I've also installed something that is supposed to be a GUI for R, but I haven't yet figured out how to run it.[/QUOTE]
```

R --gui=tk
```

I tried using gnome, but the package in the repos is empty

---

### Post by pstep9407 on 2006-10-11
I didn't like the Tk gui much so I kept looking and found Rcmdr, which is built with ... Tk! But it looks better! Does it work? We'll find out..
To try it out, do :
```
sudo apt-get install r-cran-rcmdr
```
Then, to start it, start R normally from the CL, and enter:
```
library("Rcmdr")
```
A few seconds later, you should have a working GUI. The creators of the package wrote an academic paper to accompany it -- find it at [http://www.jstatsoft.org/v14/i09/v14i09.pdf](http://www.jstatsoft.org/v14/i09/v14i09.pdf)

---

### Post by towsonu2003 on 2006-10-11
the thing is, I was interested in R when I was writing my thesis. then I found out that I cannot use it until I get an R course... at the university I mean. 

So I got stuck with spss and vmware while writing the thesis... wasn't happy...

R has so much potential. It has so much potential that you can't grasp it (letalone learn it) quickly without a nice GUI that will allow you to "play around". A nice gui with understandable menus, sensible buttons, and a "my user is stupid" attitude ;)

without such a stupid[me]-oriented gui, it seems to me that only the R-book-readers and R-class-takers will be able to use it, not those who have to "write it now and learn it later". 

ps. cmdr is very nice when compared to tk. but, weirdly, it blocks its developers from writing a gui for R, because they keep saying "hey we have a gui".

---

### Post by akniss on 2006-10-11
> **towsonu2003 said:**
> the thing is, I was interested in R when I was writing my thesis. then I found out that I cannot use it until I get an R course... at the university I mean. 

So I got stuck with spss and vmware while writing the thesis... wasn't happy...

R has so much potential. It has so much potential that you can't grasp it (letalone learn it) quickly without a nice GUI that will allow you to "play around". A nice gui with understandable menus, sensible buttons, and a "my user is stupid" attitude ;)

without such a stupid[me]-oriented gui, it seems to me that only the R-book-readers and R-class-takers will be able to use it, not those who have to "write it now and learn it later". 

ps. cmdr is very nice when compared to tk. but, weirdly, it blocks its developers from writing a gui for R, because they keep saying "hey we have a gui".


Maybe its just me, but I find Rcmdr more confusing than the cli R interface...

---

### Post by pstep9407 on 2006-10-21
Come to think of it, you're right. What I like about the OS X interface for R is not the buttons or drop-downs but the layout -- script on the right, interpreter on the left. That said, I'm working on a script, and I have a question about installing R packages on Linux. How is it done? I downloaded a package called maptools, and it's in my /tmp dir, but how to proceed from there? Any help at all would be appreciated. Tx,
Phil

---

### Post by akniss on 2006-10-21
> **pstep9407 said:**
> Come to think of it, you're right. What I like about the OS X interface for R is not the buttons or drop-downs but the layout -- script on the right, interpreter on the left. That said, I'm working on a script, and I have a question about installing R packages on Linux. How is it done? I downloaded a package called maptools, and it's in my /tmp dir, but how to proceed from there? Any help at all would be appreciated. Tx,
Phil

assuming the downloaded package is called maptools.tar.gz, and is in your /tmp directory, at a terminal, type ```
sudo R CMD INSTALL /tmp/maptools.tar.gz
```
That should take care of it.

---

