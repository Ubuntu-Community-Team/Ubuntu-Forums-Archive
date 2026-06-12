---
title: "Deb V.S RPM?"
date: 2009-03-15
forum: General Help
---

### Post by izizzle on 2009-03-15
These two seem to be the two most commonly used package managers for distros. What exactly are the differences between these two? Is one better than the other? Which do you prefer (aside from the fact that Ubuntu uses debs)? And, what is "dependancy hell"?

---

### Post by LegendofTom on 2009-03-15
When using a debian distro, I find .deb quicker and cleaner.

---

### Post by Yashiro on 2009-03-15
The best packaging format is the one your distro uses.

---

### Post by izizzle on 2009-03-15
> **Yashiro said:**
> The best packaging format is the one your distro uses.

Yes, but what if you are playing around with distros, trying to choose the one you want to stick with? Then would you consider distros that use RPM or DEB?

---

### Post by lykwydchykyn on 2009-03-15
I don't think the package formats are all that significant; It has more to do with the tools you have to work with them.  On the .deb side, APT (and it's various front-ends: apt-get, aptitude, synaptic, etc) is pretty universally used to manage packages.

On the RPM side, different distros have different tools. Suse has YAST, Fedora/RedHat has YUM, and you can apparently even use APT for RPM.  I've encountered a few other tools for RPM as well.

I've personally had better luck with dependency handling on Debian type distros, but that has more to do with the way repositories are organized and maintained than the package format.  Some people would disagree with me.

---

### Post by tgalati4 on 2009-03-15
Dependency Hell happens when you want to compile the latest version of OpenOffice 3.0 on your old Dapper Drake box.  You find that OpenOffice 3.0 isn't available for Dapper in the repositories for simple installing.

So, you download the source code and ./configure and make.

Then you quickly find that you are missing a bunch of needed libraries.

No problem, you try installing those libraries.  But they are missing from the repositories and so you download the source for those libraries and try to make them as well.  But this fails because you are missing yet more libraries.

And the cycle continues.

If you have an older box, running an older distro and you want the latest and greatest Banshee music player to run on it:  try compiling banshee from scratch and post your results.  That's Depencency Hell.

---

### Post by jimmyhacker on 2009-03-15
tgalati4 why you just use dapper drake?why you just install Hardy or Intrepid repositories and upgrade?

About RPM v.s DEB,i seen all redhat based distros are ugly ****.Ubuntu Gutsy Gibbon`s desktop is selected most beautiful desktop of 2009.

---

### Post by mb_webguy on 2009-03-15
> **jimmyhacker said:**
> tgalati4 why you just use dapper drake?why you just install Hardy or Intrepid repositories and upgrade?

About RPM v.s DEB,i seen all redhat based distros are ugly ****.Ubuntu Gutsy Gibbon`s desktop is selected most beautiful desktop of 2009.

tglati4 was just using that as an example.  Dependency hell is whenever you're trying to install something -- usually by compiling source code, but also when installing through a downloaded deb package -- and it depends on other packages which you don't have, which in turn depend on other packages you don't have, which in turn depend on other packages you don't have, ad nauseum.

---

### Post by Simian Man on 2009-03-15
> **jimmyhacker said:**
> About RPM v.s DEB,i seen all redhat based distros are ugly ****.Ubuntu Gutsy Gibbon`s desktop is selected most beautiful desktop of 2009.

What on God's green earth are you talking about?

One format isn't better than the other.

---

### Post by 3Miro on 2009-03-15
I have used debs and rpms and they both have worked for me. It is the rest of the dstro that makes my choice. Several years ago both Red Hat and Mandrake used rpms and were even 90+ percent compatible with each other, but Mandrake worked better for what  I wanted (a working system with less hassle). In terms of less hassle, IMO Ubuntu is the best thing right now, and it just happens to use debs.

One thing I am yet see in the debs that I miss from the rmps. That is source deb packages, at the same time you compile the way you want for you specific system and yet Dependency Hell is nowhere near as bad. (Then again, it it was such a big deal I would have gone with Gentoo)

---

### Post by ubuntu27 on 2009-03-15
> **jimmyhacker said:**
> tgalati4 why you just use dapper drake?why you just install Hardy or Intrepid repositories and upgrade?


tgalati4 was replying to izizzle's question.
The thing about installing a new software in a old OS was an example.

> **izizzle said:**
>  ....And, what is "dependency hell"?

---

### Post by lykwydchykyn on 2009-03-15
> **3Miro said:**
> 
One thing I am yet see in the debs that I miss from the rmps. That is source deb packages, at the same time you compile the way you want for you specific system and yet Dependency Hell is nowhere near as bad. (Then again, it it was such a big deal I would have gone with Gentoo)

Unless I'm missing something, there are source debs.  At least, you can get sourcecode using Debian package management tools.  Have you not seen "apt-src" or "apt-get source"?

Maybe not quite the same as source rpms, I don't know.

---

### Post by sgosnell on 2009-03-15
I don't think there is enough difference between the two package types to make any difference.  I've tried distros which used both, and you can't tell the difference.  In fact, Ubuntu can install .rpm packages if you first install alien, and I can't really see anything different.  You may run into dependency problems if you try to install an rpm package on a Debian distro, or vice versa, but it's not a package problem, it's a matter of the different libraries they might use.  You can get just as much dependency hell installing a .deb package in Debian or Ubuntu.  I would never let the package format determine which distro I chose.

---

### Post by elliotn on 2009-03-15
To me debs are debian, well Ubuntu is an Os Mmmm Debian, but maybe There should be an Ubuntu extensions as a special ubuntu parkage. It could be .ubu. . .

---

### Post by mb_webguy on 2009-03-15
> **sgosnell said:**
> I don't think there is enough difference between the two package types to make any difference.  I've tried distros which used both, and you can't tell the difference.  In fact, Ubuntu can install .rpm packages if you first install alien, and I can't really see anything different.  You may run into dependency problems if you try to install an rpm package on a Debian distro, or vice versa, but it's not a package problem, it's a matter of the different libraries they might use.  You can get just as much dependency hell installing a .deb package in Debian or Ubuntu.  I would never let the package format determine which distro I chose.

Just so any newbies reading this will know...  It is not advised to install rpm packages on Ubuntu (or any other Debian-based system).  Debian and Red Hat are both Linux, but they do have their differences.  Alien does what it was designed to do, but it doesn't change paths or dependencies.  You may very well run into problems when installing software from a deb converted from an rpm package.

It may not be as easy, but if a deb for some software isn't available, it's generally better in the long run to compile from source rather than convert and install an rpm.

---

### Post by sgosnell on 2009-03-15
True, but some apps only come in .rpm packages, even though they're targeted for debian forks.  It's not usual, but I've run across a couple over time.  I would certainly advise at least trying to find a .deb package if you're running Ubuntu, but as a last resort alien can help out.

---

### Post by tgalati4 on 2009-03-17
I still have Dapper running on a server box.  It works and I'm lazy.

---

### Post by Slim Odds on 2009-03-17
> **mb_webguy said:**
> Just so any newbies reading this will know...  It is not advised to install rpm packages on Ubuntu (or any other Debian-based system).  Debian and Red Hat are both Linux, but they do have their differences.  Alien does what it was designed to do, but it doesn't change paths or dependencies.  You may very well run into problems when installing software from a deb converted from an rpm package.

It may not be as easy, but if a deb for some software isn't available, it's generally better in the long run to compile from source rather than convert and install an rpm.

Well said. Noobies.... read again.

---

### Post by fieroboom on 2009-03-17
> **Yashiro said:**
> The best packaging format is the one your distro uses.

:agree:
However, IMHO, apt pwns.
I have yet to find a pkg manager that I consider competitive with apt.
:D
-Paul

---

### Post by mcduck on 2009-03-17
The biggest difference is in the tools used to manage the packages, in my opinion both dpkg and apt are way better than rpm is.

Of course the difference isn't that noticeable any more as most rpm-based distros already include some package management tool that works more or less like apt does, at least from the user's point of view.

Personally, however, I prefer .deb-based distros, probably because of all the troubles I've had with rpm packages (in times before GUI tools, when apt definitely was far better than tools you had on RPM-based distros).

---

### Post by izizzle on 2009-03-17
So it seems that .debs are generally easier to work with compared to .rpms. And, Other than that, no significant dfferences are distinctable.

---

### Post by 3Miro on 2009-03-20
I don't think it is a deb version general, just deb distros maybe have more intuitive tools. The entire goal of Ubuntu is to make it run as easy as possible, if Ubuntu has using rmps it would have still been the same great OS and in that case debs would have been harder to work with.

In general one should not install rpms on Ubuntu. There are some cases when you have no choice, but that should be your last resort. For example, my canon came with drivers only in the rpm form and there was no choice but to use alien. So alien is the last resort only.

---

### Post by Vorian Grey on 2009-03-20
> **mcduck said:**
> 
Of course the difference isn't that noticeable any more as most rpm-based distros already include some package management tool that works more or less like apt does, at least from the user's point of view.


Exactly. I use Ubuntu and openSuse and there is very little difference in the package system in general use.

---

