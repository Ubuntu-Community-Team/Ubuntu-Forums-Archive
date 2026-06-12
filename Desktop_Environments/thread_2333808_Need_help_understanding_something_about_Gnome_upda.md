---
title: "Need help understanding something about Gnome updates."
date: 2016-08-13
forum: Desktop Environments
---

### Post by noobkill on 2016-08-13
Hello.

I'm running Ubuntu Gnome 16.04.1 and i understand the things about release timelines etc, so i'm absolutely not complaining that it didn't ship with the newest version of gnome.
But what about udates? Will there be any? And what about manual upgrade? Why is it not recommended? 
What if i was to install a linux distro without any DE and installed newest Gnome on it after? Is that safer than an update?

Ps. I'm a linux noob, switched from Windows few weeks ago and i love it.

---

### Post by CatKiller on 2016-08-13
16.04 is a Long Term Support release, which means that it in principle gets extra time for testing before release. LTS releases rarely have the absolute newest versions of software. There are periodic point releases that include newer versions of selected software.

The version of Gnome included with 16.04 isn't particularly old, 3.20 having only been released a couple of weeks before 16.04. Some parts of 3.20 have already been backported.

Which features do you think you're missing?

---

### Post by noobkill on 2016-08-13
Hi.

Thanks for a quick answer.
Like i said I'm not really missing anything, and I'm happy with the system as it is, it's just that when I was doing some reading online, I saw that a lot of people are not recommending upgrading to a new version since there are risks of bugs etc.
So that got me thinking why would there be bugs? If a stable software got released and is available why is it not recommended?
And again I would like to say that I'm not trying to complain :) I did a lot of distro jumping before I finally settled on Ubuntu Gnome and I'm happy, I just wanna understand what is it that makes upgrading so risky in Linux systems?

---

### Post by Frogs Hair on 2016-08-13
There will be updates to the current version in use, but you will not get an upgrade to Gnome 3.20 . The Gnome 3 team PPA's are available , but are use at your own risk. 

[https://launchpad.net/~gnome3-team/+archive/ubuntu/gnome3-staging](https://launchpad.net/~gnome3-team/+archive/ubuntu/gnome3-staging)

> === *WARNING* ===
The packages here have been deemed not ready for general use, they have  known bugs and/or regressions, sometimes of a critical nature. Mostly  things should run smoothly but be prepared to use ppa-purge, when you  encounter issues!

 If they break your system, you get to keep both halves.


---

### Post by kurt18947 on 2016-08-13
> **noobkill said:**
> Hello.

.....................................................

Ps. I'm a linux noob, switched from Windows few weeks ago and i love it.

Have you discovered extensions.gnome.org yet? There are a few extensions I consider mandatory, they make gnome-shell work like I prefer. You have to be a little bit careful because some extensions with similar function will conflict.

---

### Post by noobkill on 2016-08-13
> **kurt18947 said:**
> Have you discovered extensions.gnome.org yet? There are a few extensions I consider mandatory, they make gnome-shell work like I prefer. You have to be a little bit careful because some extensions with similar function will conflict.

Yes I saw it and i really like what some of the extensions can do :)

---

### Post by grahammechanical on 2016-08-13
We need to understand the concept of "upstream" and "downstream."

Ubuntu is built on the Gnome 3 desktop environment (DE). So, Gnome 3 DE is upstream to Ubuntu. Any updates to packages in Gnome 3 DE come downtream to Ubuntu and as Ubuntu is upstream to the Ubuntu flavours built on Ubuntu (such as Ubuntu Gnome) those same updates that are put into Ubuntu will also go into Ubuntu Gnome and the other flavours because they all use the same software repositories. This situation is also true when it comes to the Linux kernel and certain applications like Firefox and Libreoffice.

Ubuntu uses the Unity shell. Ubuntu Gnome uses the Gnome 3 shell. So, in the case of the shell (user interface) in Ubuntu Gnome Ubuntu itself is not an "upstream." This means that the small group of Ubuntu Gnome developers have to do the work of bringing upstream Gnome 3 shell improvements into Ubuntu Gnome. We call all this kind of stuff "updates."

> I just wanna understand what is it that makes upgrading so risky in Linux systems?

Now, that is a different question. Upgrading from one version to an newer version is not risky if.

1) We are using the default OS and have not modified the user interface excessively.
2) we have reverted to using an open source video driver instead of a proprietary video driver.
3) we have disabled all PPAs and in some cases purged the PPA to remove the packages the PPA brought in. This applies in particular to the Gnome 3  PPAs being mentioned.

> === Removing ===
Use ppa-purge to remove this PPA. It is *particularly* important to do this before upgrading to a new release!

 ppa-purge gnome3-team/gnome3-staging
ppa-purge gnome3-team/gnome3



[https://launchpad.net/~gnome3-team/+archive/ubuntu/gnome3-staging](https://launchpad.net/~gnome3-team/+archive/ubuntu/gnome3-staging)

4) do not leave the upgrade unattended. It might need user interaction.
5) do not get bored and power off the machine or if it is a laptop, shut the lid.
6) keep children & cats away from the machine.

Based on the number of people asking on this forum for help after upgrading, some of us are inclined to the view that a fresh install is best.

On the subject of stability and bugs, please remember that we have an OS that is free to download, install, use and distribute. A lot of work is done by volunteers. This is especially true of testing the pre-release versions and the upgrade process. More testing = fewer bugs in the "stable" release = need more testers.

Anyone one can test. No special skills needed. We even have a section on this forum for discussing any issues we come up against. It is the Ubuntu Development Version section.

Regards.

---

### Post by noobkill on 2016-08-13
Thank you so much @grahammechanical.

Your explanation clears up a lot of things.
So basically some software just has to be "adapted" before use to ensure stability etc.

Thanks again for the explanation.

---

