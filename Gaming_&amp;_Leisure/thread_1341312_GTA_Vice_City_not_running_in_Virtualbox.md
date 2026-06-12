---
title: "GTA Vice City not running in Virtualbox"
date: 2009-11-29
forum: Gaming &amp; Leisure
---

### Post by olvlo on 2009-11-29
Hi, everybody. I have installed Virtualbox 3.0 ('closed' source) to run a XP host inside my UbuntuStudio system. I am trying to run Grand Theft Auto: Vice City (original) to no avail: The program installs with no problems, but when I try to run it, the pointer changes to a spinning CD and then nothing happens. I even tried to run it from the command prompt, with no error message.

Has anybody had a similar problem or knows how to solve it?

My system specs (within Vbox):

MS Windows XP Professional Service Pack 3
Total Physical Memory: 319.48 MB
Available Physical Memory: 121 MB
Total Virtual Memory: 2 GB
System Manufacturer	innotek GmbH
System Model	VirtualBox
System Type	X86-based PC
Processor	x86 Family 15 Model 76 Stepping 2 AuthenticAMD ~2199 Mhz
BIOS Version/Date	innotek GmbH VirtualBox, 12/1/2006
SMBIOS Version	2.5

Running Virtualbox 3.0 on Ubuntu Studio 8.04 (32-bit)
Kernel 2.6.24-25-rt
Memory: 1.9 GB
Processor: AMD Turion 64 Mobile Technology MK-38


Thanks for any help ypu can provide!

Regards,
olvlo

---

### Post by CharmyBee on 2009-11-29
Vice City is a Direct3D game. Virtualbox only virtualizes OpenGL.

---

### Post by meborc on 2009-11-29
according to this - [http://appdb.winehq.org/objectManager.php?sClass=version&iId=3050](http://appdb.winehq.org/objectManager.php?sClass=version&iId=3050) you should get the game working in WINE

there is no need to install windows in virtualbox... you can't run 3d in virtual environment (yet anyway)

use wine+game ;)

---

### Post by BigSilly on 2009-11-30
It does work beautifully in WINE, I can vouch for it! ;) You just have to press a button to skip the video at the beginning, because it just pauses there instead of playing it. Otherwise perfect though.

---

### Post by olvlo on 2009-11-30
Dear CharmyBee, meborc and BigSilly,

Thanks a lot for your replies; I see the problem. I'll give it a try with Wine! Thank you very much!

---

### Post by Glucklich on 2009-11-30
VirtualBox is not advisable, nor built, for games. Well, at least, that resource consumptive games. I believe one could play GTA2 in VirtualBox if he wanted. But in this situation, like previous posters have advised, use Wine.

---

### Post by CharmyBee on 2009-11-30
> **Glucklich said:**
> VirtualBox is not advisable, nor built, for games. Well, at least, that resource consumptive games. 

There's this neat technology called AMD-V that speeds virtualization up by 4000% I hear. VirtualBox supports it.

(Yes, it does make it possible, though (OpenGL) games like SoF2 actually have timing problems for running too fast, even on maximum detail.)

---

### Post by Glucklich on 2009-11-30
> **CharmyBee said:**
> There's this neat technology called AMD-V that speeds virtualization up by 4000% I hear. VirtualBox supports it.

(Yes, it does make it possible, though (OpenGL) games like SoF2 actually have timing problems for running too fast, even on maximum detail.)

Didn't knew about that. I went looking for it and found out that it is on specific processors. So, for now, it is as useless as it gets until you buy a new computer and keep that in mind. But as you said, it is pretty neat.

---

