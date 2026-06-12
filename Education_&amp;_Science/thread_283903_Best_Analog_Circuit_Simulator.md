---
title: "Best Analog Circuit Simulator"
date: 2006-10-24
forum: Education &amp; Science
---

### Post by boz on 2006-10-24
I'm fairly new to Linux.  I've been using Ubuntu for about a year now.  I'm also not a complete n00b to programming, but my C++ is quite rusty and deplorable in its present condition.  I've tried some of the circuit simulators in the repository but I'm not completely satisfied with them for analog simulations.  Maybe I'm used to all the bells and whistles included in Pspice Schematics which is no longer supported.  I'm trying to look for an adequate replacement of the aforementioned simulator.

I've heard some promising things about tclspice, but I had trouble compiling it.  Mainly, I had dependency issues, but the instructions are rather cryptic as well.  Has anyone tried tclspice?  How did you get it working?  Is it an effective analog simulator with plenty of bells and whistles?  (I need plotting functions, and lots of them.  DC, AC, transient, etc.)  If not, I may have to wine the Student version of Pspice Schematics.  :roll: I prefer to stay in the Linux environment as much as I can, however.  (I dual boot with Windows, but I'm only on it when I need to run a network simulator that has no dual in Linux.)

---

### Post by boz on 2006-10-27
Judging from the number of responses here, there are probably not of electronics/computer engineers on this forum, but I'm having great success with gEDA so far so I thought I'd share anyway.  I wouldn't get it from the repos, however.  Get it from [here]("http://www.geda.seul.org/download.html").  You can download the .iso file there.  I know you have to have kernel header files, build-essential, and gtk2 source files installed for sure.  If you have other dependency problems, you'll have to read the documentation, but I didn't have any other problems beyond those.  The CD takes care of most of your dependencies.  You do have to mount the cd with the -o option as well.  The online documentation walks you through that.

---

### Post by ChristophM on 2006-11-08
How does wine work? 

I'm trying to get completely independent from Windows, but [http://www.linear.com/company/software.jsp](http://www.linear.com/company/software.jsp) (LTSpice, to be precise) is a strong reason to emulate Windows under Linux, so I'd be thankful for any hints you might be able to give. 

Christoph

---

### Post by hammad1337 on 2007-11-27
wine <file.exe>

If wine is not installed:
sudo apt-get install wine

---

