---
title: "change graphics settings on login"
date: 2009-02-19
forum: General Help
---

### Post by NinjaWork on 2009-02-19
Hi everyone,

When I boot the computer, I don't have a splash screen but rolling text of information. What file do I need to edit to make this look better...change font, etc?

Thanks

---

### Post by gdonwallace on 2009-07-31
In case you have not gotten an answer on this one yet.  In order to get the splash screen back you need to edit your menu.lst file. 

menu.lst is located in /boot/grub/.  Make a backup before you make any changes.  Towards the end of the file are the lines that cause GRUB to react the way it does on boot up.  There is one entry for each line on your GRUB menu.  If you have not made any changes AND are running 9.04 then GRUB should have 3 entries.  The first entry is the standard boot.  In order to get the splash back, add the word splash to the end of the line that starts kernel:

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		51bb9228-c16f-4aec-b14d-260a0d01ead9
**kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=51bb9228-c16f-4aec-b14d-260a0d01ead9 ro xforcevesa quiet _splash_ **
initrd		/boot/initrd.img-2.6.28-11-generic

---

### Post by egalvan on 2009-07-31
StartupManager also manages these, but in a GUI window...
much safer if you are nervous around the cli.

---

