---
title: "Clean install of 10.10 on Inspiron m101z?"
date: 2011-01-30
forum: Dell Ubuntu Support (CLOSED)
---

### Post by echo59 on 2011-01-30
Hi,

I've bought a Inspiron m101z which came pre-installed with Windows 7 64-bit and Ubuntu Light as a dual-boot.  AMD Athlon ii K325, 4GB RAM, 320GB HDD.  I have no optical drive, but have boot from USB enabled.  The Ubuntu Light seems to be a network version of Ubuntu 10.4.

 

I want to install the desktop version of Ubuntu 10.10 in my Linux partition instead of Ubuntu Light.  I've been having difficulty doing this.  I've tried to get the desktop version of 10.4 but there are problems and it failed twice.  Some of the issues include that I cannot update the Broadcom driver, I cannot delete the USA keyboard as the default keyboard layout and I get frequent crashes.  Also, I cannot connect to my wireless network, despite using the confirmed key.

 

At this stage, I want to try a clean install of 10.10 and I want to know how to remove Ubuntu Light from the laptop.  In the current setup, I tried to boot from a Live USB of 10.10 but instead it booted to Ubuntu Light on the 2nd boot...

 

I'd appreciate any help.

 

J

---

### Post by mikewhatever on 2011-01-30
You should definitely post the output of the [BootInfoScript]("http://sourceforge.net/projects/bootinfoscript/") before anyone tries helping you. Basically, we need to know the partition layout and the bootloader situation.

---

### Post by echo59 on 2011-01-30
Thanks a million, I've attached the output from BootInfoScript in the file RESULTS.txt

---

### Post by mikewhatever on 2011-01-30
Right, so this should be pretty straight forward. To boot from the 10.10 usb, change the boot order in the bios. Once booted, I suggest testing the hardware for a while to make sure everything works. Then, to make space for the new installation, delete the sda4 partition, and resize the W7 partition to make more space (about 25GB is ok).
As always, when editing partitions and installing OSs, have a good backup as well as a restore strategy.
You could also do a wubi installation, which doesn't involve messing with partitions.

---

