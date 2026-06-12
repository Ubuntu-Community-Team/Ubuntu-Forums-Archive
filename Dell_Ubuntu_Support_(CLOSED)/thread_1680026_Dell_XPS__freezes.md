---
title: "Dell XPS  freezes"
date: 2011-02-01
forum: Dell Ubuntu Support (CLOSED)
---

### Post by vinodc on 2011-02-01
Hi Guys,

I have a dell XPS for almost an year and I have installed Ubuntu from the day 1 I got it and have been updating regularly ie installed 9.10 upgraded to 10.04 and now running 10.10.  I have been updating / upgrading the packages whenever a new version is available.

Now I am experiencing a strange problem that the machine just freezes occasionally and it need to be rebooted to gain access again. I have isolated the following nature of the issue

1. It happens within 10 minutes of machine starts 
2. It is happening only when the power is turned off or not connected. 
3. It is not happening in windows. 

I feel the issue is with some power management packages but I cannot isolate the issue 

Thanks for your help!
Vinod

---

### Post by mörgæs on 2011-02-03
Yes, there have been some bugs regarding power management. If nobody has a better advice I guess the obvious solution is to stay with 10.04 or try a clean install of 10.10.

---

### Post by FFuser on 2011-02-05
Hi, I'm having similar problems today (at fosdem)

I'm having the new Dell XPS 15 (i7 model). I only had problems when (re)connecting to the wireless system. There seemed only a problem when trying to reconnect, and not on the first connect after boot (or turning hardware wireless on/off).

This is on a clean 10.10 install

---

### Post by vinodc on 2011-02-05
hmm, I have done a reinstall of almost all power management packages and it seems to be ok now ( touchwood ) - doing some testings... 

went to synaptic, searched for " power" on top right and then reinstalled all the installed ones :-s ( not specific fix but it seems working now ) ... worked on the lappy for a few times without power and it didnt freeze 

thanks for your inputs, @FFuser and mörgæs  :)

vinod!

---

### Post by russom on 2011-02-07
I've had an XPS M1330 for several years and I have always run Ubuntu in a dual-boot configuration with the Vista system that came with the machine.  I recently upgraded to Windows 7 (I did a clean install) and then installed Ubuntu 10.04 along with the GRUB loader.

Both systems run well, but when I shutdown Ubuntu and then startup in Windows, the mouse pad does not work; i.e., I have to shutdown and startup twice to get the mouse pad working in Windows after running Ubuntu.  

Starting up in Ubuntu is never a problem.

What am I doing wrong?

---

### Post by xghstst0riesx on 2011-02-07
russom, you should start a new thread about your touchpad issue since it's not related to freezing. You might get more help that way. 

I also have this problem. It's not reliably reproducible but it seems to happen to me the most when connecting my USB printer. I've also had it happen when connecting a USB external hard drive and when I've restarted with the printer connected. I've already looked in syslog and there doesn't appear to be anything relevant in there. Does anyone know if there's a way to enable more detailed debugging for either USB or power management? Or has anyone seen any bugs already filed that seem related?

I'm using a Studio XPS 16 with Core i5 and Radeon HD5730 1GB.

---

### Post by mörgæs on 2011-02-08
> **russom said:**
> I've had an XPS M1330 for several years and I have always run Ubuntu in a dual-boot configuration with the Vista system that came with the machine.  I recently upgraded to Windows 7 (I did a clean install) and then installed Ubuntu 10.04 along with the GRUB loader.

Both systems run well, but when I shutdown Ubuntu and then startup in Windows, the mouse pad does not work; i.e., I have to shutdown and startup twice to get the mouse pad working in Windows after running Ubuntu.  

Starting up in Ubuntu is never a problem.

What am I doing wrong?


If you have not done recently, then you could try to upgrade the BIOS as a first step.

If that does not work best is to open a new thread, as xghstst0riesx mentioned.

---

### Post by mörgæs on 2011-02-08
> **xghstst0riesx said:**
> russom, you should start a new thread about your touchpad issue since it's not related to freezing. You might get more help that way. 

I also have this problem. It's not reliably reproducible but it seems to happen to me the most when connecting my USB printer. I've also had it happen when connecting a USB external hard drive and when I've restarted with the printer connected. I've already looked in syslog and there doesn't appear to be anything relevant in there. Does anyone know if there's a way to enable more detailed debugging for either USB or power management? Or has anyone seen any bugs already filed that seem related?

I'm using a Studio XPS 16 with Core i5 and Radeon HD5730 1GB.

Which version of Ubuntu are you using?

---

### Post by xghstst0riesx on 2011-02-08
> **mörgæs said:**
> Which version of Ubuntu are you using?

I'm on 10.10.

---

### Post by FFuser on 2011-02-08
> **vinodc said:**
> hmm, I have done a reinstall of almost all power management packages and it seems to be ok now ( touchwood ) - doing some testings... 

went to synaptic, searched for " power" on top right and then reinstalled all the installed ones :-s ( not specific fix but it seems working now ) ... worked on the lappy for a few times without power and it didnt freeze 

thanks for your inputs, @FFuser and mörgæs  :)

vinod!

Today I went totally crazy and installed kernel 2,6,38-rc4 from [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.38-rc4-natty/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.38-rc4-natty/) and I'm running some time now on battery, without any trouble.

Even reconnected to my wireless several times, suspended to disk etc.I hope it stays that way...

---

### Post by mörgæs on 2011-02-09
> **xghstst0riesx said:**
> I'm on 10.10.

These USB errors can be hard to trace. Trying the new kernel like FFuser and a new BIOS as suggested above are my best ideas.

---

### Post by xghstst0riesx on 2011-02-21
I've tried a newer kernel and that didn't help. It did stop freezing after I installed a 2.6.34 kernel from the kernel PPA. I filed a bug on launchpad: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/721954]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/721954").

---

### Post by beruic on 2011-02-22
What graphics does the M1330 owners have, and do you update drivers from PPA?
I had an issue with freezing some time ago. It disappeared after removing the updates from [https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates).

---

### Post by beruic on 2011-02-22
I have Intel graphics btw.

---

### Post by bongey on 2011-03-05
Have the exact same problem on my xps 16. Driving me nuts. Going to try a later kernel. 

My machine froze 3 times in a row. 
The wireless sometimes was working other times it was not.

What wireless card does everyone have? 

The dells can come with an intel or dell module. I have the 
id:	
network
description: 	Wireless interface
product: 	Ultimate N WiFi Link 5300
vendor: 	Intel Corporation
physical id: 	
0
bus info: 	
pci@0000:05:00.0
logical name: 	
wlan0
version: 	00
serial: 	00:21:6a:81:42:3c
width: 	64 bits
clock: 	33MHz
capabilities: 	pm msi pciexpress bus_master cap_list ethernet physical wireless
configuration:	
broadcast	=	yes
driver	=	iwlagn
driverversion	=	2.6.35-27-generic
firmware	=	8.24.2.12

from lshw

---

