---
title: "Problems with Dell and ubuntu and vista"
date: 2007-07-18
forum: Dell  Ubuntu Support
---

### Post by xq1024 on 2007-07-18
Hi,

I had recently bought a DELL inspiron 640M notebook, Windows Vista Home Premium. I intended to have a dual boot with linux Ubuntu. I had referred to the guide from [http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first](http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first). I have set up unallocated space to the system for the installation of ubuntu. It was until the step to double click the install icon in the welcome page, my system stops halfway during the installation process. I restarted the system. but this time, my system cannots boot into the original vista. It complains that there is no bootable device found.

I have also tried to reinstall and recover my notebook to its factory state with the vista DVD provided with the dell system, but was unable to as when they are installing the vista, it complains there is no driver found. 

currently i cannot access the window vista.

Please guide me on how to solve this matter as i would need this for my college assignments. Thanks in advance.

---

### Post by PeggySue on 2007-07-18
Hi,
I suggest you reinstall Vista first.  On the Dell you need to have the recovery DVD in the machine.  Switch on and as the BIOS does its thing repeatedly tap F12.  The boot device menu should appear.  This doesn't require any driver from the hard drive; just a functioning PC!
From the boot menu select the CD ROM option.  The DVD should then talk you through the recovery.

You can then install Ubuntu.  The installer comes with a repartitioning tool.  You could try that.  But don't be put off by a long pause during install.  It took my machine the best part of an hour to install.

You might like to have the PC always check the DVD for a bootable cd/DVD.  This is usefull to run Live Linux CDs.  To do this you need to repeatedly hit F2 during bootup and change the BIOS.  Not difficult but don't rush it and don't do anything you don't understand.  Fixing the BIOS is tricky!

Good Luck

---

### Post by strabes on 2007-07-18
I don't think you have to reinstall vista. The ubuntu CD probably messed with your MBR (master boot record.) GRUB is probably not installed or something. Try downloading the alternate install CD, booting, & installing from that. If the installation is successful, grub will be installed and will also automatically detect your windows partition so when you boot your computer you will be presented with a menu that allows you to choose which operating system to boot.

---

### Post by mpospisil on 2007-07-18
I would try taking a look at this link. Hopefully this helps. [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

