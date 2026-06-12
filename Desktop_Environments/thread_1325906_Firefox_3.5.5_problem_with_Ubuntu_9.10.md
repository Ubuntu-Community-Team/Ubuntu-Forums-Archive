---
title: "Firefox 3.5.5 problem with Ubuntu 9.10"
date: 2009-11-13
forum: Desktop Environments
---

### Post by keithld on 2009-11-13
Until 3 days ago I was running a Dual Boot with WinXP & Ubuntu 8.10 then while in Windows AVAST antivirus decided that: c:/ubuntu/disks/root.disk was the Trojan win32:banload - ST [trj] and decided to delete it... Sooo I had no more Ubuntu... I uninstalled WUBI and then Installed Ubuntu 9.10 and it works great...

The Problem: I notice that most of my bookmarks load like instantly and some that have may 10-20 thumbnails or many pics load the site the the images take a minute or more to load... firefox also acts this way in *Safe Mode*....i.e. firefox safe-mode

So while in a Terminal I was watching Firefox in safe mode load a site that was having problems and this code came up in the terminal over and over again....

**(firefox 8387): Gdk-warning **: XID Collision, trouble ahead**

So what is the problem????

Thanks guys,

Keith

---

### Post by wojox on 2009-11-13
Are you using any add ons like speed dial?

---

### Post by keithld on 2009-11-13
Adblock Plus 1.1.1

CoolPreviews 2.7.6.0623

FaviconizeTab 0.9.8.2

McAfee SiteAdvisor 28.0

Quickrestart 1.1.5

SearchPreview 4.0

Ubuntu Firefox Modifications 0.8

WOT 2009128


Now that I think about it it could be CoolPreviews... Or maybe not....


Nope wasn't CoolPreviews, just turned it off and rebooted no change...

I also tried firefox safe mode and *Disabled All Addons* no difference...  Maybe it's my ISP but in Windows XP it is quite a bit faster and the images load quickly...

---

### Post by garvinrick4 on 2009-11-14
Here is bug. I believe there was a fix down towards bottom of that Page


[https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/401823](https://bugs.launchpad.net/ubuntu/+source/firefox-3.5/+bug/401823)

---

