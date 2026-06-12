---
title: "xfce 4.8, xubuntu distribution the perfect candidate?"
date: 2011-12-13
forum: Desktop Environments
---

### Post by francois.e on 2011-12-13
Since the event of xfce 4.8, different distributions have decided to implement this most recent version of the desktop environment flavor to their distribution. It would be interesting to compare xubuntu with other distribution inplementing the xfce 4.8 version. No distribution could be perfect, but what would be the best balanced one?

Given your experience since the outing of xubuntu on 10.04 with xfce 4.8 what is your opinion in terms of xubuntu for the following criteria?

1) fast bootup speed (like slackware and its derivative)
2)  the possibility of passing thru login manager directly into the X  environment for a given user (even as root user) (this is not possible  with debian)
3) the use of a recent kernel and a simple and efficient  strategy for problematic wifi and graphic drivers (bcm, nvidia) and  dual display settings (as good ubuntu or mint)
4) an efficient os in  terms of printer implementation (this is not the case with slackware  that seems to be troublesome with brother printer drivers under CUPS,  amongst others)
5) a broad access to a variety of software (ubuntu or debian like)
6) ease of installation
7) reliability

---

### Post by markMDW on 2011-12-13
Xfce 4.8 came out on 1/16/2011.  I noticed that Xubuntu 10.04 booted quicker and  noticeable more responsive than 11.04.  Could the reason be that 10.04 used Xfce 4.6 while 11.04 used 4.8 (I'm guessing that 4.8 would have been implemented by then)?   Also, 11.04 failed to install on one challenged PC-- it would never boot after installation) 10.04 installed just fine on it. 

Otherwise the ease of installation, variety of software and reliability are excellent, and in many ways superior to standard Ubuntu.  One exception is that over the years I've experienced one specific glitch while using Xubuntu on various machines:  The mouse cursor disappears from the desktop sometimes, unpredictable after going to screensaver.    The pointer location of the mouse still exists in memory; I can tell this from moving the mouse around the desktop in the hopes of spotting it.  I never do, but various text fields and icons will highlight as I hover over them.  That's good enough to exit and reboot the computer and that's the only way to get the mouse cursor visible again.   Logging in and out doesn't solve the problem either.  This glitch existed as of 10.04 but I can't say that its still an issue in later versions because Ive always elected to reinstall using the long term support version, 10.04 version.

One HUGE item I wish Xubuntu and Xfce could implement:  Have a graphical response effect of some sort when clicking on a desktop program icon.  Once I double click on one, and wait a while, I frequently double click again to make certain that the double click was successful and not interpreted by the computer as two single clicks.  If I did double-click the program icon I find out only later when the program launches twice.  As it stands there is no way for the user to know if he sent a double-click on top of the icon or (mistakingly) two single-clicks.  This is a frustrating scenario and whenever it happens it makes the user think less of the operating system.    Waiting long spans of time waiting for the program to open up is frustrating when the user realizes they only issued a single click.  The advice to users: 'you should be more careful' when clicking an icon is worthless if your goal is getting them to *enjoy* the operating system.  Why should a user have to be careful when doing something very easy like activating the program they want to activate.  It should be effortless or else the operating system will be judged poorly compared to another operating system that actually engineers it to be truly effortless.

Other than that network browsing inside the Thunar File Manager is my top issue.   I understand this has been taking care of in Xfce 4.8 though.

Comparison to Gnome:
I think the Xfce Settings Manager is vastly superior to the Gnome methods of fine tuning the desktop environment, which isn't even logically at times.  Imagine, why in the world would it be expected from a new user that to change the system Fonts, Themes or Visual Effects you have to: Right-Click on Desktop, then select<Change Desktop Background>.   Most would think that this selection applies for what it indicates, the 'wallpaper'.   As Shuttleworth pointed out several releases ago, there were many little 'paper-cuts'  to users experiences with Gnome.  Thanks my review

---

### Post by ernestj on 2011-12-13
> **markMDW said:**
> Xfce 4.8 came out on 1/16/2011.  I noticed that Xubuntu 10.04 booted quicker and  noticeable more responsive than 11.04.  Could the reason be that 10.04 used Xfce 4.6 while 11.04 used 4.8 (I'm guessing that 4.8 would have been implemented by then)?   Also, 11.04 failed to install on one challenged PC-- it would never boot after installation) 10.04 installed just fine on it. 

Otherwise the ease of installation, variety of software and reliability are excellent, and in many ways superior to standard Ubuntu.  One exception is that over the years I've experienced one specific glitch while using Xubuntu on various machines:  The mouse cursor disappears from the desktop sometimes, unpredictable after going to screensaver.    The pointer location of the mouse still exists in memory; I can tell this from moving the mouse around the desktop in the hopes of spotting it.  I never do, but various text fields and icons will highlight as I hover over them.  That's good enough to exit and reboot the computer and that's the only way to get the mouse cursor visible again.   Logging in and out doesn't solve the problem either.  This glitch existed as of 10.04 but I can't say that its still an issue in later versions because Ive always elected to reinstall using the long term support version, 10.04 version.

One HUGE item I wish Xubuntu and Xfce could implement:  Have a graphical response effect of some sort when clicking on a desktop program icon.  Once I double click on one, and wait a while, I frequently double click again to make certain that the double click was successful and not interpreted by the computer as two single clicks.  If I did double-click the program icon I find out only later when the program launches twice.  As it stands there is no way for the user to know if he sent a double-click on top of the icon or (mistakingly) two single-clicks.  This is a frustrating scenario and whenever it happens it makes the user think less of the operating system.    Waiting long spans of time waiting for the program to open up is frustrating when the user realizes they only issued a single click.  The advice to users: 'you should be more careful' when clicking an icon is worthless if your goal is getting them to *enjoy* the operating system.  Why should a user have to be careful when doing something very easy like activating the program they want to activate.  It should be effortless or else the operating system will be judged poorly compared to another operating system that actually engineers it to be truly effortless.

Other than that network browsing inside the Thunar File Manager is my top issue.   I understand this has been taking care of in Xfce 4.8 though.

Comparison to Gnome:
I think the Xfce Settings Manager is vastly superior to the Gnome methods of fine tuning the desktop environment, which isn't even logically at times.  Imagine, why in the world would it be expected from a new user that to change the system Fonts, Themes or Visual Effects you have to: Right-Click on Desktop, then select<Change Desktop Background>.   Most would think that this selection applies for what it indicates, the 'wallpaper'.   As Shuttleworth pointed out several releases ago, there were many little 'paper-cuts'  to users experiences with Gnome.  Thanks my review



I think this is a known bug. I saw another post about this. I was able to fix it by doing this: right click desktop and -> properties -> permissions -> group access - opt. read & write.

This helped, but the problem, if I remember correctly is the way Thunar searches. If I can find the post I will link it to this post. I think the problem will be solved by 12.04.

Anyways, Xubuntu is the best.

---

### Post by francois.e on 2011-12-17
Amongst those who worked with both 11.04 and 11.10 version of xubuntu with xfce 4.8 on the desktop, does 11.10 represents an improvement?

---

### Post by LewisTM on 2011-12-19
> **francois.e said:**
> Amongst those who worked with both 11.04 and 11.10 version of xubuntu with xfce 4.8 on the desktop, does 11.10 represents an improvement?

I found virtually no difference between both releases. The switch to LightDM seems to be the only big change and that is not Xfce-specific. For me it fixed some Compiz bugs but introduced new ones.

It's still a plus to upgrade because a number of other apps have been updated. Don't forget that if you don't upgrade, and unless you have a custom PPA for an app or there is a major bug-fix release, you will be forever stuck with the same versions of the apps as initially installed.

This has to be weighed every six months against the chance of breaking the system by upgrading, which is getting kind of tiresome.

---

### Post by 2F4U on 2011-12-19
I found not much difference between 11.10 and 11.04 except for newer versions of software. Even the wallpaper seems to be the same. But that is not a bad thing in my opinion, since both are running stable on my machines.

---

### Post by snowpine on 2011-12-19
You may find this poll interesting. :)

[http://linuxblog.darkduck.com/2011/12/users-voted-for-best-xfce-based-linux.html](http://linuxblog.darkduck.com/2011/12/users-voted-for-best-xfce-based-linux.html)

---

### Post by francois.e on 2012-01-10
The result of the abovementioned post is interesting. But does it reflect reality of the performance of xfce or only the preference for one basic distribution or another: ubuntu and mint being the most performant distributions in the polls.

The following threas is about people trying xfce across the different distributions:
[http://forum.xfce.org/viewtopic.php?id=5926](http://forum.xfce.org/viewtopic.php?id=5926)

I would be surprised after looking at the thread to read your conclusions.

---

### Post by LewisTM on 2012-01-10
> **francois.e said:**
> The result of the abovementioned post is interesting. But does it reflect reality of the performance of xfce or only the preference for one basic distribution or another: ubuntu and mint being the most performant distributions in the polls.

The following threas is about people trying xfce across the different distributions:
[http://forum.xfce.org/viewtopic.php?id=5926](http://forum.xfce.org/viewtopic.php?id=5926)

I would be surprised after looking at the thread to read your conclusions.
My conclusion is that there are lots of hackers out there, Linus Torvalds included, who use XFCE on their Arch or Gentoo box. These people are always looking for ways to squeeze every last bit of speed from their system and have strong ideological opinions about what is a "pure" distro whether or not that helps performance and usability. 
Xubuntu is not targeted at these users.

---

### Post by francois.e on 2012-01-12
I hope that antiperformance is not the goal of xubuntu:)

---

