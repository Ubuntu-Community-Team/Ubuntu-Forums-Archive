---
title: "Drivers/software instalations"
date: 2009-03-27
forum: General Help
---

### Post by Renigade on 2009-03-27
First off: I am a complete noob to Ubuntu.

Rather then assume it is ok to install drivers and programs in any order I thought I would Ask first.

I'm on a fresh Install of Ubuntu Desktop 8.04.2 X64 Dual booting With XP pro X64 installed first on a 500GB SATA (Drive partition split 250gb for each)  then Installed Ubuntu desktop 8.04.2
I have downloaded 1 set of updates through FireFox and installed/rebooted.

My system:
Gigabyte MA709X DS4 w/Phenom 9850 BE~ 500GB SATA~ Aopen DVD/R/RW optical ~ ATI Radeon HD 4870.

I am going to run Ubuntu mainly to Fold.

Programs I want to run/install: But have no clue if some of them are necessary. Also have no clue if there is a particular order that  any of this would need to be installed.
Motherboard/Chipset/processor drivers?
ATI CCC/drivers
wine
F@H Monitor
FAH SMP
FAH GPU client

I hope I didn't leave anything out. 
1) where do I start?
2) in what order?

Thanks in advance: DaN00b :lolflag:

---

### Post by Renigade on 2009-03-27
Bump?

---

### Post by mb_webguy on 2009-03-27
In general, drivers are included in the Linux kernel, and you don't need to install them.  If you have any doubts about your hardware working under Linux, boot the LiveCD.

As for those programs, if they are available in the Ubuntu repositories or are available as deb files (which are sort of like exe or msi installers in Windows), then the programs will install themselves in the appropriate order.  And if you don't have all of the dependencies for a program installed, the program won't let you install it.

Since you're going to have to install the F@H client from source code, I'd suggest using [auto-apt and checkinstall]("https://help.ubuntu.com/community/CheckInstall").  This will automatically download and install any dependencies, and create a package to allow you to manage the software in a package manager like apt or Synaptic.

---

