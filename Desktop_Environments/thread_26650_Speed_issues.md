---
title: "Speed issues"
date: 2005-04-13
forum: Desktop Environments
---

### Post by elias4444 on 2005-04-13
I've been using Debian and Ubuntu both, and have noticed a pretty serious difference in speed on the same machine when switching between the two. Particularly, two things stand out:

1. The whole Gnome GUI seems to be substantially slower in Ubuntu. Response times, window dragging, basically the whole of it. I'm not sure why this is. On Debian, the system is very snappy, with great response times and very fluid window movement. Is this an Xorg/Gnome-2.10 issue?

2. My network speed is absolutely terrible on Ubuntu compared to Debian. Doing some file transfer benchmarks over sftp on a local LAN revealed that Ubuntu transfers at a max rate of 300kb/s, whereas Debian is at 2000kb/s!!! Web browsing and other "typical" uses also seem to be effected.

Anyone know what's going on? I've gone back and forth between Debian and Ubuntu, and my findings are consistent. My test machine is as follows:

Dell Latitude C810
512MB memory
Pentium 3(mobile) 1.13ghz processor
40gb HD (DMA is enabled by default)
3Com (3c59x) ethernet
Nvidia Geforce2Go
1600x1200 native resolution

---

### Post by shakin on 2005-04-13
GUI lag might be caused by different video drivers. Perhaps Ubuntu made an incorrect choice when installing the system, in which case you should file a bug report.

Have a look at the X config files on both systems and make sure the video drivers are the same. While you're there check the loaded modules and any options that may be configured for the video card. I suspect that maybe Ubuntu is using a vesa driver, although even vesa isn't slow on my system.

---

### Post by elias4444 on 2005-04-13
Sorry about that... I should specifiy:

I used the newest Nvidia drivers (7174) on both machines.
I also tried the basic nv drivers, but things were even worse.

---

### Post by elias4444 on 2005-04-19
Can anyone confirm what I'm seeing on their own systems?

---

### Post by speedman on 2005-04-19
I recently moved my laptop from Sid to Hoary (something I never thought I would ever do as a long term Debian user) and my xorg.conf was absolutely butchered by Hoary.  I ended up using my XF86Config-4 from Sid with no changes and simply renaming it xorg.conf and everything went back to working normally.  It might be worth trying the same thing in your case.

With regards to network performance I would suggest turning of ipv6 to see if your situation improves.

Edit /etc/modprobe.d/aliases and change alias net-pf-10 ipv6 to alias net-pf-10 off.

HTH


Regards,

SM

---

### Post by lazychris2000 on 2006-03-13
i know this is a rather old post, but maybe this will help someone else who is searching for an answer.

In regards to the slow performance with X, I have found that if you boot off a live cd and check the performance then copy the xorg.conf (if everything is smoother) onto your installed system.  This has saved me much time and trouble when I hope my system for whatever reason.
I'm not sure how important this is, but you will probably want to boot off the same version live cd as the distro you have installed (get a breezy cd if youre running breezy, etc).  This may save you from having incompatibilities with 2 different versions of X.

---

