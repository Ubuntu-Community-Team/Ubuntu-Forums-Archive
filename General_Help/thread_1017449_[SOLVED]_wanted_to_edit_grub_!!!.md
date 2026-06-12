---
title: "[SOLVED] wanted to edit grub !!!"
date: 2008-12-21
forum: General Help
---

### Post by chinmaya_n on 2008-12-21
I updated my system few hours back ..... it didnt gave me any problem. But when i restared it i saw two extra options in the grub menu.... which are repeated..... I'm using Ubuntu 8.10 LTS. The first options is to select ubuntu 8.10 and the second is to perform recovery mode. These two are repeated twice....and Mem Test is single.

can anyone help me to remove those extra lines >> guide  me to edit the grub... plzz...!!:)

---

### Post by PocketDog on 2008-12-21
Easy fella, just copy ```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak
``` into a terminal which creates a backup of your current grub, then copy this ```
gksudo gedit /boot/grub/menu.lst
```
and paste into a terminal. You can then safely remove any entries you don't want. Any line starting with **#** will be ignored as a comment rather than a command. When you're finished, save and reboot

---

### Post by chinmaya_n on 2008-12-21
Thank u "pocketdog" ............ it worked ....!!!

Thanks 4 clear explanation.

---

### Post by Elfy on 2008-12-21
Just like to add that in grub the lines before ## ## End Default Options ## which are preceded by # are NOT ignored - they are used by update-grub for kernel updates - lines there need ## to be ignored.

---

### Post by drs305 on 2008-12-21
Here's a link that explains it - why you see the extra entries and the options you have for dealing with them. It also discusses a handy gui-based app called StartUp-Manager which can tweak a lot of grub's settings, such as menu display timeout, default kernel/OS, how to update, menu colors, etc.
[HOWTO: Grub Menu Kernel Display Options]("http://ubuntuforums.org/showthread.php?t=818177")


When you don't have any other questions for this thread please mark the thread 'Solved'.

---

