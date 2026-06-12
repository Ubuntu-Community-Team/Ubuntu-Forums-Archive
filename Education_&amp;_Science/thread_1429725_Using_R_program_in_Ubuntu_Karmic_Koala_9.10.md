---
title: "Using R program in Ubuntu Karmic Koala 9.10"
date: 2010-03-14
forum: Education &amp; Science
---

### Post by xcrunner78 on 2010-03-14
Hi,

I was wondering if anyone uses R statistical program out there.  I was searching for the vegan package, that I use quite frequently and was wondering if it is available for R using Linux.  Any help would be greatly appreciated.

-Jason

---

### Post by memilanuk on 2010-03-14
I was going to suggest doing a search on the forum here, but I'm guessing searching for a single letter might give the search engine fits.

If you look back through a handful of pages of this forum and you'll probably see R mentioned a time or two.  I may be mistaken, but I believe Linux (specifically Debian) is one of, if not *the* primary development platform for R, so pretty much any package should be available on Linux if its available anywhere.

---

### Post by gunksta on 2010-03-14
I just upgraded all of my systems to 10.04 so I can't be 100% positive, but I am 99.999% positive that the answer is - No. Fortunately, it's easy to confirm this for yourself.

```
apt-cache search vegan
```

Throw that at a terminal on your computer. It will tell you if there are any packages with the word vegan in them (including the description). When I ran this on my system, I got nada.

I'm afraid that install.packages() is your friend. Given your first post, you probably already know how to do this.

---

### Post by whelanh on 2010-03-14
I run Lucid Lynx, but this should apply for your version also.  I Googled "R vegan" and got this site: [http://cc.oulu.fi/~jarioksa/softhelp/vegan.html](http://cc.oulu.fi/~jarioksa/softhelp/vegan.html) 

Based on this, it is very easy to install.  In a command terminal:

1) Type "sudo R" (use sudo so you can install packages)
2) Then per web page above, type "install.packages("vegan",repos="http://r-forge.r-project.org")"   
3) After it installs, you can load with "library(vegan)"

Hopefully I didn't misunderstand your question, but it appears to be easy to load into R.

Best,
Hugh

---

### Post by memilanuk on 2010-03-14
I don't think he meant an Ubuntu package, but an 'R' package... unless cran2deb has been ported to Ubuntu?

install.packages() shows a listing for 'vegan' on the Windows port of R; I can't imagine why it wouldn't be available on all (I don't think any of the packages within R are platform-specific?).

---

### Post by myotis on 2010-03-14
If you go to [http://cran.r-project.org/](http://cran.r-project.org/) and then choose Linux and then choose ubuntu  you will find instructions to set up the backport for R.

Once set up then install.packages ("vegan") works. I've just done it.

Graham

---

### Post by anoop999 on 2010-03-14
Use the command **install.packages()** from within R - it will first show a dialog box asking you to choose the download mirror, then a list of available packages on CRAN. The **vegan** package is in the list, I just checked.

---

### Post by xcrunner78 on 2010-04-08
Hey, sorry for the late reply, I for some reason stopped getting e-mail notifications for replies on this forum.  But thanks for solving my dilemma !  :)

---

