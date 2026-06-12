---
title: "Need help setting up a multiboot"
date: 2009-05-24
forum: General Help
---

### Post by ali999 on 2009-05-24
Hi

I am trying to setup a multiboot on my computer. I currently have a dual boot with vista and ubuntu using GRUB as my boot loader. I am interested in installing the new windows 7 RC so i can test it out but am not sure how I should go about setting this up so that all my old operating systems remain as they are. I also want to keep GRUB as my bootloader. I have two internal discs installed on my computer currently, one with all the OS's and one with all my data. I would prefer to keep all the OS's on the same discs. Has anybody tried something like this before? If so, how do you go about setting something like this up? Any help would be greatly appreciated. Thanks

---

### Post by bhishan on 2009-05-24
First create a NTFS partition in your OS drive. Install Windows 7 in that partition. This will delete GRUB.

Boot into the live Ubuntu cd. This can be the live installer cd or the older live session Ubuntu cds.

When you get to the desktop open a terminal and enter. (I am going to give you the commands and then I will explain them later)

Code:

sudo grub

This will get you a "grub>" prompt (i.e. the grub shell). At grub>. enter these commands

Code:

find /boot/grub/stage1

This will return a location. If you have more than one, select the installation that you want to provide the grub files.
Next, THIS IS IMPORTANT, whatever was returned for the find command use it in the next line (you are still at grub>. when you enter the next 3 commands)

Code:

root (hd?,?)

Again use the value from the find command i.e. if find returned (hd0,1) then you would enter root (hd0,1)

Next enter the command to install grub to the mbr

Code:

setup (hd0)

Finally exit the grub shell
Code:

quit

That is it. Grub will be installed to the mbr.
When you reboot, you will have the grub menu at startup.

---

