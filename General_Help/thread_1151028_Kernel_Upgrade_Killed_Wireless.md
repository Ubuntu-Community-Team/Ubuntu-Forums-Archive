---
title: "Kernel Upgrade Killed Wireless"
date: 2009-05-06
forum: General Help
---

### Post by Prominence on 2009-05-06
Please help me, my wireless driver was removed or something with the latest upgrade, it couldn't install the restricted modules if that's what's causing the issue, if you can help me, please do, and quickly

---

### Post by prem1er on 2009-05-06
Why weren't you able to install the restricted drivers?

---

### Post by snowpine on 2009-05-06
Impossible to help if we don't know which wireless card you're using. :)
The terminal command 'lspci' (without the quotes) will show exactly which chipset you have. Then, the search function on these forums will help you find more info.
Also we need to know which Ubuntu release (Hardy, Intrepid, Jaunty, etc) and kernel version to have any chance of helping.

While you are waiting, you should be able to boot into your old kernel from the Grub boot menu so you can keep working.

---

### Post by Prominence on 2009-05-06
I don't know why it didn't install, I'm not an expert, but I just need to get things going again. 

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
02:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)
09:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
09:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
09:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
09:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
09:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
grayson@iGrayson:~$

---

### Post by snowpine on 2009-05-06
Broadcom bcm4312 is the same card I use (Dell Mini 9). It should work out of the box in Ubuntu 8.10 or 9.04; you might have to go to the System Menu->Hardware Drivers to enable the restricted driver.

If you are not using Intrepid or Jaunty with the "stock" kernel, you can get the module you need here: [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

---

### Post by Prominence on 2009-05-06
The restricted stuff couldn't install therefore I can't enable it, and I dont know how to install .tar.gz files whatsoever

---

### Post by prem1er on 2009-05-06
> **Prominence said:**
> The restricted stuff couldn't install therefore I can't enable it, and I dont know how to install .tar.gz files whatsoever

Again, what do you mean by the 'restricted stuff couldn't install'? Were there errors? What happened?

---

### Post by Prominence on 2009-05-06
Linux Restricted Modules Generic 

There must've been an error, tried installing it via Synaptic and said

linux-restricted-modules:
  Depends: linux-restricted-modules-generic (=2.6.28.12.16) but 2.6.28.11.15 is to be installed

---

### Post by colau on 2009-05-06
> **Prominence said:**
> The restricted stuff couldn't install therefore I can't enable it, and I dont know how to install .tar.gz files whatsoever
You can try this.
[html]
tar vzxf filename.tar.gz
[/html]
Now going to that filename directory(this may need being root)
[html]
./configure
make 
make install
[/html]

---

### Post by SoCalChris on 2009-05-06
I'm not sure if this is related, but I just tried doing an update and am getting dependency errors with the linux-generic package. It's possible that was uninstalled, and is causing your errors.

```
The following packages have unmet dependencies:
  linux-restricted-modules-generic: Depends: linux-restricted-modules-2.6.28-12-generic which is a virtual package.
The following actions will resolve these dependencies:

Remove the following packages:
linux-generic

```

---

### Post by snowpine on 2009-05-06
Sounds like you are not the only one having this problem today (gee isn't the Search feature wonderful):

[http://ubuntuforums.org/showthread.php?t=1150498&highlight=BCM4312](http://ubuntuforums.org/showthread.php?t=1150498&highlight=BCM4312)
[http://ubuntuforums.org/showthread.php?t=1150481&highlight=BCM4312](http://ubuntuforums.org/showthread.php?t=1150481&highlight=BCM4312)

My advice is to just boot into the old kernel from Grub until they fix this for you.

It is not your fault; you didn't do anything wrong--someone dropped the ball.

---

### Post by snowpine on 2009-05-06
> **colau said:**
> You can try this.
[html]
tar vzxf filename.tar.gz
[/html]
Now going to that filename directory(this may need being root)
[html]
./configure
make 
make install
[/html]

This will not work in this case; you have to follow the instructions in README.TXT exactly, however, I do not recommend it in this case as I'm sure it's just a temporary bug (sounds like they pushed the kernel through updates but not the modules yet)... simply booting into the old kernel for now is the easiest fix.

---

### Post by Prominence on 2009-05-06
Ok...I hope this is fixed soon, I have no clue about any of this, way over my head

---

