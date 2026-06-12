---
title: "text mode at startup (Xubuntu 6.06)"
date: 2007-01-24
forum: Desktop Environments
---

### Post by arepisky on 2007-01-24
Hello,

I have changed my xorg.conf to add a keyboard layout and made some error in it. Xfce refused to start. I have restored the old xorg.conf but now xfce does not start at startup. I get only text mode login prompt. I have to login and type startx each time at startup.

I would like xfce to start immediately after computer starts. Please help me.

                           Andrej

---

### Post by rabid emu on 2007-01-24
Go into /boot/grub/menu.lst and make sure your xubuntu bootup isn't booting into single-user mode.

---

### Post by arepisky on 2007-01-24
Here is the first entry in menu.lst:

title           Ubuntu, kernel 2.6.15-26-386
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.15-26-386 root=/dev/hda3 ro quiet splash
initrd          /boot/initrd.img-2.6.15-26-386
savedefault
boot

I think it is something else. There should be some file telling what commands to run at boot time. Adding startx there could perhaps help.

BTW how do I set up auto login? I am former Debian user and the Debian graphical login could be easily adjusted to log certain user in at startup.

---

