---
title: "GRUB Geom error after winxp fixmbr"
date: 2006-10-07
forum: Desktop Environments
---

### Post by bartbes on 2006-10-07
I always had a slow boot with GRUB. And about a week ago I couldn't boot Win XP anymore, error "GRUB Geom Error" when I choose Windows XP.
I decided to install LILO, works perfectly for booting linux, but when I boot windows, I get the GRUB Geom Error again. I booted from my Win XP install cd and did both fixboot and fixmbr. And still I get the GRUB error. Even when I boot directly from IDE0 (my 20GB winxp drive).

How can I remove GRUB from my MBR?

---

### Post by bartbes on 2006-10-12
I really need this! I've done everything which could repair it, winzp fixboot and fixmbr (as I said in my previous post) I also tried fdisk /mbr. I figured something else out, if I boot from my first HD (where GRUB was installed), it tries to write my boot sector first.

---

### Post by wwwOyster on 2007-10-26
My setup
WinXP on Primary hdd.
Ubuntu v7.10 on Secondary USB hdd.

Problem:
When I remove the USB drive, I cannot boot into Windows. I of course then udnerstood that the GRUB boot loader was stored on the USB Drive, and was required.

Dilemma -- I needed to boot to WinXP professional, without having the USB HDD attached.

Solution -- OSL2000. This is a powerful boot loader, that replaces the GRUB loader, and provides access to either partition. It was very powerful, and the TIP at the end -- uninstalling OSL2000 does a clean uninstall & replaces the primary drive's MBR with a correct copy for WinXP. (I found OSL2000 here - [http://mentalpagingspace.blogspot.com/2005/08/fixing-mbr-after-grub-install.html](http://mentalpagingspace.blogspot.com/2005/08/fixing-mbr-after-grub-install.html))

This was a 3 day effort of pain .. and a 30s solution from OSL2000. Hope this helps others.
Thanks,

---

