---
title: "reasons for compiling fluxbox?"
date: 2007-02-22
forum: Desktop Environments
---

### Post by RedSquirrel on 2007-02-22
Hi all,

As you can probably tell from my signature, I am an avid Fluxbox user. I am currently using the package from the repositories but I have been thinking about compiling it from source. 

I have my own reasons for compiling it, but for those of you who have done this (or plan to in the near future), what were your reasons? 

- using the bleeding-edge source files? 
- bug testing? 
- choice of compile options?
- fun & glory?


Thanks for any responses.

---

### Post by scooper on 2007-02-22
For me, mainly to get the latest version when there was a large skew between the pre-packaged versions and the latest from fluxbox.org.  I don't think the packages lag as badly as they used to, so I'm not compiling these days.  I also look at the source code to develop some related tools, but otherwise I wouldn't bother building from source.  I've never seen perceptible performance differences on reasonably recent hardware.

---

### Post by yabbadabbadont on 2007-02-23
I was, hmmm, experimenting yesterday and ended up reinstalling, so I'm not currently using Fluxbox.  However, I normally build it from the latest svn code.  The Fluxbox devs are very good about not checking in code that won't build, and it usually doesn't cause problems.  I like to build the svn version because there are quite a lot of bugfixes being added every week.  Just use the web-svn viewer at the berlios.de fluxbox repository to view the Changelog.  It gets updated regularly (even when the docs don't ;)) and is a good way to find out about new options/features/bug fixes.  Plus, since I use checkinstall to build a deb package and then install from there, it is easy to test the newest svn code and then roll back to the previous version when needed.  I've only had to roll back once in the last year or so of updating from svn once a week.  (Now if I could only say the same about E17...  :D)

---

### Post by sessine on 2007-02-28
I'm currently trying to compile fluxbox, however, when I run 'configure' it gets so far through and then says:
```
checking for X... no
configure: error: Fluxbox requires the X Window System libraries and headers.

```
Since I currently have Gnome desktop I must have the X libraries but could it be that they are (somehow) not in the place fluxbox is looking?

:confused:

---

### Post by yabbadabbadont on 2007-02-28
> **sessine said:**
> I'm currently trying to compile fluxbox, however, when I run 'configure' it gets so far through and then says:
```
checking for X... no
configure: error: Fluxbox requires the X Window System libraries and headers.

```
Since I currently have Gnome desktop I must have the X libraries but could it be that they are (somehow) not in the place fluxbox is looking?

:confused:

You have the libraries, but you don't have the development libraries....  They are two different sets of packages in Debian based systems.  (one of the things I miss from Gentoo by the way)  Install xorg-dev and then also run, "sudo apt-get build-dep fluxbox", to install any other dev libraries that may be needed, but not installed by xorg-dev.

---

### Post by sessine on 2007-03-01
Thanks, installing those extra packages fixed the compile error.

---

### Post by RedSquirrel on 2007-05-03
A small update...

The version of Fluxbox in the repos is now a little old so for me it is nice to be able to use the latest version by compiling it myself.

Just thought I'd add as well that doing "sudo apt-get build-dep fluxbox" is sufficient to satisfy all dependencies for the fluxbox source. To compile the SVN code, I also grab libtool, automake1.9, subversion, and subversion-tools. [EDIT: checkinstall is _very_ important as well when compiling.]

---

### Post by yabbadabbadont on 2007-05-04
> **RedSquirrel said:**
> [EDIT: checkinstall is _very_ important as well when compiling.]

Only when it works.  :)

Read the docs on its homepage for instances in which it doesn't work correctly.  (python based apps, for instance, can cause trouble)  However, it does work correctly with Fluxbox.  As long as you make sure to set the installation prefix directory to /usr/local when you run configure, it isn't strictly necessary though.

---

### Post by RedSquirrel on 2007-05-05
> **yabbadabbadont said:**
> Only when it works.  :)

Read the docs on its homepage for instances in which it doesn't work correctly.  (python based apps, for instance, can cause trouble)  However, it does work correctly with Fluxbox.  As long as you make sure to set the installation prefix directory to /usr/local when you run configure, it isn't strictly necessary though.


Quite right. I guess I meant that checkinstall was important when compiling *Fluxbox* because it allows you to remove and install different versions so easily (as you mentioned above). Thanks for the clarification. I have heard of some of its strange behaviour. :)

The configure script sets the installation prefix to /usr/local by default, which is convenient. checkinstall fails if you set a different prefix?

---

### Post by RedSquirrel on 2007-05-13
Well, as it turns out, "sudo apt-get build-dep fluxbox" is *not* sufficient for compiling the Subversion version. It worked with 4872, but 4882 failed until I installed xorg-dev. All is well now. Another "tip of the hat" to yabbadabbadont. :)

---

### Post by yabbadabbadont on 2007-05-16
> **RedSquirrel said:**
> Another "tip of the hat" to yabbadabbadont. :)

Sign above toilet in men's room, "We aim to please.  You aim too, please."  :D

---

