---
title: "Install ubuntu alongside kubuntu?"
date: 2016-07-26
forum: Desktop Environments
---

### Post by LK_gandalf_ on 2016-07-26
Hello, I have installed kubuntu 16.04 on a laptop. It si sowkring ok, but it is quite slow and lagging, probably because of the ATI graphic card (proprietary drivers are no longer available, it seems...).
I was thinking to try ubuntu, and wondering what is the cleanest way to install it and, eventually, remove it and go back to kubuntu.
I have made a lot of configurations on the kubuntu desktop, so I would like to keep them.
Thanks! :)

---

### Post by ajgreeny on 2016-07-26
Do you have specification good enough to use a Virtual installation?

Preferable to have a dual, or better, quad core machine and 4 or 8GB RAM.

I use VirtualBox from their own repos, version 5.0.26, though version 5.1.# is also available but had a few problems for me; I could not enable USB-2 with it for some items. See the **Debian-based Linux distributions** section of [https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads) for details of how to add those repos if you want to try it and get the same version of the Extension Pack (Guest Additions) from [https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads) .

I have Ubuntu 16.04 running fine on my desktop machine using Xubuntu 14.04 as host; the unity desktop is running very well and I fgind it difficult to see any difference in speed of the system from a "real" hardware installation.

If your machine spec is not up to running VBox or similar you will need to set up a normal dual boot but how you do that is a bit more complicated and depends on your machine's BIOS/UEFI and current setup, ie partition layout etc etc.

Come back again if you want to pursue this further with a lot more info about your machine and current setup

---

### Post by LK_gandalf_ on 2016-07-29
Hi, and thanks for the nice reply. Unfortunately that's not possible because the laptop has only 2gb ram, it's 5 years old. It has windows 7 and a normal bios. 
I think kubuntu would run nice, but the issue is graphic drivers, and it seems there is nothing to do since ATI and ubuntu have dropped the proprietary drivers starting 16.04, before they have developed a proper alternative. Also the power management is not working: no battery detected, no suspension, no proper shutdown. These issues could be fixed in the future, but per now the performances are very poor.

At this point I am considering formatting and installing kubuntu 14.04 LTS, not many other choices :( I guess all the line-up 16.04 has this issue with the graphic drivers and the power management. Not sure trying ubuntu 16.04 would make a difference in terms of hardware support.

---

### Post by ajgreeny on 2016-07-29
You are correct that the ATI/AMD graphics situation is less that brilliant for *ubuntu 16.04 versions, but it is unfair to blame Ubuntu for that situation; it is more down to AMD.

They are, however, presently working hard on new versions of open-source drivers for their cards, either the radeon or amdgpu drivers that will work with the version of xorg in 16.04 and new hardware.  

It will come, but I have no idea on time-scale for this to happen, so for the moment you are stuck with the radeon driver that should have been installed when the OS was.  I hope you did not try to install the proprietary driver for your card, or that if you used fglrx in the past you removed it fully before upgrading.

What does terminal command ```
sudo apt-cache policy fglrx
``` show as output?

Trying 16.04 of any of the *ubuntu family will not help as they all have the same problem at the moment, so don't bother with Ubuntu which needs very good graphics at the best of times for the unity desktop

---

### Post by LK_gandalf_ on 2016-07-29
Thanks, very good help :)
The output says nothing installed. I am sure they will improve the situation in the future, so maybe I could try 15.10 instead of 14.04, and eventually upgrade later on. Not sure :)

---

### Post by ajgreeny on 2016-07-29
15.10 will lose support in August (just a few weeks) so is not really a good alternative to 14.04.
EDIT:
Just realised that my timing of August was too late; 15.10 lost support yesterday, July 28.

As you can see from my signature I am still using 14.04, but Xubuntu in my case, which is incredibly stable, and the same is true, I believe, of all the other 14.04s in the group.  That would be my recommendation unless you can live with the graphics glitches of 16.04 until AMD ups their game.

---

### Post by LK_gandalf_ on 2016-09-11
Hi, unfortunately Kubuntu 16.04 is still working bad, so I will try to format and put 14.04 LTS ;) It's quite old but I guess it's ok for a normal home use.

---

### Post by mörgæs on 2016-09-11
Kubuntu 14.04 is fine to use for all users, both business and home users, through april 2017. As always, apply all updates and you are good to go.

---

