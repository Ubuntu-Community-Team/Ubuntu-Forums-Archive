---
title: "Dell Inspiron 1150 Wireless"
date: 2007-08-08
forum: Dell  Ubuntu Support
---

### Post by ponderosajoe20 on 2007-08-08
Hello Everyone,

I just installed Ubuntu 7.04 on my Dell Inspiron 1150.  I am very excited to start using it but have a problem with the internal wireless card.  I have read some of the posts regarding installation of the drivers but being a newbie to Ubuntu its mostly greek to.  Is there a simple way to install the necessary drivers?  I believe I have a Broadcom BCM4306 wireless card.  Anyone wanna help?

ponderosajoe20

---

### Post by EdTheUniqueGeek on 2007-08-08
I have the same card in my C400 that I am seeking WPA help on.

See thread:
[http://ubuntuforums.org/showthread.php?t=519223]("http://ubuntuforums.org/showthread.php?t=519223")

The card actually works well in a initial install of Ubuntu 7.04, except for WPA. I've been able to connect to WEP access points with no problem right after the install.
However, I would recommend installing and using Wicd as your network manager.

[http://wicd.sourceforge.net/]("http://wicd.sourceforge.net/")

I have found it to be a better manager than the default Gnome network manager.

---

### Post by EdTheUniqueGeek on 2007-08-08
I read this incorrectly. My bad. I thought you stated you had the Truemobile 1150 in your Inspiron. I need to read closer next time.
However, I would still recommend Wicd.

---

### Post by ponderosajoe20 on 2007-08-08
Does this have the required drivers to make it work?  The wireless card is a 1350 Mini PCI Card by Broadcom using the BCM4306 chipset.

---

### Post by EdTheUniqueGeek on 2007-08-08
If that TM 1350 is not working in the default install of Feisty, which I am surprised it is not, then you might want to install ndiswrapper, grab the latest Dell wireless drivers from Dell's site (you'll need a Windows machine to extract the files), and use ndiswrapper to install those drivers.
I'm no expert by far but that would be the first thing I would try. You can go into Synaptic Package Manager under Preference (I think - trying to recall as I am not in front of my Ubuntu machine right now) and search for ndiswrapper. Once it is listed, select the check mark and then apply. Once it is installed the ndiswrapper utility will be listed at the bottom of Administration (I think). Then use this utility to reference the folder the Dell drivers are in.
Try that. I sure someone else has a better solution but I would try that first.

---

