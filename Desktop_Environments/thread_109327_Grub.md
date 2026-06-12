---
title: "Grub"
date: 2005-12-28
forum: Desktop Environments
---

### Post by bigken on 2005-12-28
Hi I have a duel boot system ie ubuntu and winxp (MCE) every time I boot into window and then reboot I get the **grub loading stage1.5. grub loading, please ****wait.... error 5** I have repaired this error using the ubuntu disc and rewriting the grub menu but evry time i boot into windows this happens any ideas :confused

I also have the same setup on 3 other PCs with no problems:rolleyes:

---

### Post by psusi on 2005-12-28
Looks like windows is clobbering the stage 1.5 loader located in the space between the MBR and the first partition.  Do you have an antivirus program installed in windows?

You might try reinstalling grub without using the stage 1.5 loader.  Are you by chance, using reiserfs for ubuntu instead of ext3?  And do you have a seperate /boot partition?

---

### Post by bigken on 2005-12-28
No I dont have any virus software installed (yet) partions are 
20gb ntfs Windows media Edition
6gb fat32 Empty
50.8gb ext3 Ubuntu 
2gb linux-swap


did a winxp repair install and restored grub fix prob :D

---

