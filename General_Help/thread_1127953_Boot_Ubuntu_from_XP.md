---
title: "Boot Ubuntu from XP:"
date: 2009-04-17
forum: General Help
---

### Post by schmickey on 2009-04-17
History: 
1. Installed XP, installed Acronis True Image 2009 "Secure Zone" for backups (it's a recovery partition you are given the option to start at boot-up by pressing F11).

2. Installed 9.04 RC in unallocated space.  GRUB takes over the MBR and puts XP, Acronis Secure Zone, and XP in the GRUB boot menu.

3. The "Press F11" to enter the recovery process is gone, but the option is on the GRUB menu.lst. If I choose it, I'm told it's a non-system disk.

I can boot into XP, but not Ubuntu or the recovery partition at this point.  So, I start the True Image program and it tells me the recovery partion (Secure Zone, as it calls it) is no longer active. I activate it and there goes the GRUB menu since now XP's (or actually, Acronis' bootloader) is now in charge and I can't boot into Linux anymore.

It seems my only option to have all 3 is to somehow add Ubuntu to the boot.ini but I'm not knowledgeable enough to do that. I've "googled" it and come up with too many different options and I'm stuck.

Can I delete the Ubuntu partitions (with Partition Magic) and re-install Ubuntu with the option to put GRUB somewhere besides the MBR and have it listed in boot.ini?

Any ideas here?  Any help would be appreciated because I'd like to have the option to boot into the recovery partition if necessary and still be able to use Ubuntu and XP.

---

### Post by Merk42 on 2009-04-17
Haven't tried it myself, but I **think** EasyBCD may do what you want

[http://neosmart.net/blog/2006/easybcd-151-released/](http://neosmart.net/blog/2006/easybcd-151-released/)
[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

---

