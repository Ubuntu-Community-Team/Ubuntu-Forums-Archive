---
title: "How do I add another linux distro?"
date: 2005-11-15
forum: Desktop Environments
---

### Post by almostlinux on 2005-11-15
I'm already dual booting XP and Breezy .. and I want to install Slackware 10.2 ... 

i have a 12GB ext3 partition (and about 500 MB swap space) for this purpose

how do i make grub take care of the three OSs? I heard slackware uses LILO as it's boot manager .. would it remove grub if i install it?

---

### Post by edurm on 2005-11-15
[QUOTE=almostlinux]I'm already dual booting XP and Breezy .. and I want to install Slackware 10.2 ... 

i have a 12GB ext3 partition (and about 500 MB swap space) for this purpose

how do i make grub take care of the three OSs? I heard slackware uses LILO as it's boot manager .. would it remove grub if i install it?[/QUOTE]


Yes, Slackware 10.2 has LILO and It has lots of bugs, I think you can install slackware snf LILO. After that you can enter in ubuntu boot recovery mode and re-install grub, [ready here ](http://www.ubuntuguide.org/#restoregrubmenuafterwindowsinstallation)

---

### Post by wrtrdood on 2005-11-15
You can boot Slack via grub just fine.  Only thing is you'll need to add it to /boot/grub/menu.lst manually.  I usually just copy an existing entry (such as the one for the default Ubuntu boot) and change the various parameters.

Be sure to skip the lilo install or put it anywhere except the MBR.

---

### Post by almostlinux on 2005-11-17
since i'm installing slack....can i use the same swap space i'm using for ubuntu? i mean swap is used only when the OS is running right?

---

### Post by Hairy_Palms on 2005-11-17
yes 1 swap partition no matter how many distros you install.

---

