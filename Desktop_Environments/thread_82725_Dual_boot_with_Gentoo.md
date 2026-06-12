---
title: "Dual boot with Gentoo"
date: 2005-10-27
forum: Desktop Environments
---

### Post by jackuto on 2005-10-27
hi, if just get myself a copy of ubuntu, my pc still running on gentoo, so could i get some help how to make my gentoo to boot ubuntu?

thanks for the trouble...

---

### Post by mykey on 2005-10-27
easiest - not most elegant way to do it:

 - install ubuntu on a free partition 
 - at the end of the installation process choose to install grub on the partition you just installed the system NOT in the mbr (hd0,0 or hda)
 - go to the configuration file of your boot loader in gentoo (should be grub too) and add the entry to boot your newly installed ubuntu

---

