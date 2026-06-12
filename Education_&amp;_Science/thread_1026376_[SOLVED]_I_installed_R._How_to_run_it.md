---
title: "[SOLVED] I installed R. How to run it?"
date: 2008-12-31
forum: Education &amp; Science
---

### Post by tetrafuran on 2008-12-31
I found a huge pile of r-xyz files in synaptics. I just installed r-base and the files connected to it. Later on after some forum searching I fond out that I am supposed to install the package r-recommended. Apparently that was included in r-base... I suppose it's correctly installed.

Nevertheless now I'd like to use the program. How do I do that? Applications -> education -> has nothing new. I also noticed that some people have made "front ends" for R. I wonder if I have to research that area too. I thought the original R already contained a GUI.

It seems R isn't a proper keyword so searching this topic accurately is nearly impossible.

---

### Post by myotis on 2008-12-31
The easiest way is to run from terminal by simply typing R.

There is no GUI by default on Linux (Windows and Macs have a limited GUI interface)

You can install and run Rcmdr from the terminal which will then give you a good graphical interface, and RKward is another popular alternative on Linux. A google on either of these should fnd appropriate help.

If you google for R Cran, you will get the main R web site and there are several very good downlaodable tutorials for R available.

There are also dedicated R search engines available:

[http://finzi.psych.upenn.edu/search.html](http://finzi.psych.upenn.edu/search.html)

and

[http://www.rseek.org/](http://www.rseek.org/)

Hopefully that will get you started.

Graham

---

### Post by mali2297 on 2008-12-31
To run R in the standard command line interface, open a terminal and type
```

R

```
Note capital letter.

---

### Post by tetrafuran on 2008-12-31
I installed r-cran-rcmdr. It didn't make any icons. No prob. Let's install some more stuff. rkward did what I expected of it. Thanks.

---

### Post by myotis on 2008-12-31
> **tetrafuran said:**
> I installed r-cran-rcmdr. It didn't make any icons. No prob. Let's install some more stuff. rkward did what I expected of it. Thanks.

Rcmdr doesn't actually produce any icons it runs a GUI on top of R. 

Now that it is installed you need to run R then type in 

library(Rcmdr)

at the R prompt. 

This will either run the GUI or return you to the prompt. If returned to the prompt then type Rcmdr and hit return (sorry I cant remember how it works and I'm not at a Linux box to try it)

Its worth while perservering with Rcmdr as its Menu system is probably more extensive that rkward and as you can see the commands that Rsmdr is generating, its a good way of learning R.

Graham

---

### Post by earlycj5 on 2009-01-05
> **myotis said:**
> 
Its worth while perservering with Rcmdr as its Menu system is probably more extensive that rkward and as you can see the commands that Rsmdr is generating, its a good way of learning R.

Graham

Hmm??  Rkward is an R IDE, at least the way I use it I see all the commands that R uses because I typed them there.  But it does make working with script files and searching help BUNCHES easier.

---

### Post by myotis on 2009-01-06
> **earlycj5 said:**
> Hmm??  Rkward is an R IDE, at least the way I use it I see all the commands that R uses because I typed them there.  But it does make working with script files and searching help BUNCHES easier.

Well, yes you would, but I assumed the request for an R GUI implied a menu system, and the menu system is more extensive on Rcmdr tan rkward.

Graham

---

### Post by earlycj5 on 2009-01-06
> **myotis said:**
> Well, yes you would, but I assumed the request for an R GUI implied a menu system, and the menu system is more extensive on Rcmdr tan rkward.

Graham

Point taken, I've never used a menu system in any of the R GUIs, guess I'm a bad one to ask as I never make that jump as you did.  :)

---

### Post by myotis on 2009-01-06
> **earlycj5 said:**
> Point taken, I've never used a menu system in any of the R GUIs, guess I'm a bad one to ask as I never make that jump as you did.  :)

They are a useful steppig stone for my students who have never used a command line. 

Having said that, and several do continue using Rcmdr long term, they are much more amenable to the command line than I thought they would be. And they quickly appreciate how much more efficient the command line is.

Graham

---

### Post by euler_fan on 2009-01-07
Or, if you like Emacs + ESS is a way to go . . . I know plenty of people consider that harder than some of the other graphical interfaces, but it's got its advantages.

---

### Post by myotis on 2009-01-07
> **euler_fan said:**
> Or, if you like Emacs + ESS is a way to go . . . I know plenty of people consider that harder than some of the other graphical interfaces, but it's got its advantages.

I suspect this is the best long term option, but probably not what most people would think of as being GUI for R.

But I suspect that depends on whether you come from Unix/Linux where you are comparing it to Terminal, or coming from Windows/Macs where you expect GUI to provide full menu access to all operations/functions. 

Graham

---

