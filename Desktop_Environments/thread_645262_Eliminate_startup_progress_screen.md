---
title: "Eliminate startup progress screen"
date: 2007-12-19
forum: Desktop Environments
---

### Post by movrshakr on 2007-12-19
During bootup, there is the graphical orange progress bar and an "Ubuntu" logo.  Is there any way to have this not display and see the scrolling text of "what's happening?"

---

### Post by santaslittlehelper on 2007-12-19
Yes, edit out "quiet splash" in you're menu.lst

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
gksudo gedit /boot/grub/menu.lst
```

Change -

> title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,1)
kernel          /vmlinuz-2.6.22-14-generic root=UUID=a4fac0f5-25aa-48a3-8c11-5cc4c4382bb4 ro quiet splash
initrd          /initrd.img-2.6.22-14-generic

to -

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,1)
kernel          /vmlinuz-2.6.22-14-generic root=UUID=a4fac0f5-25aa-48a3-8c11-5cc4c4382bb4 ro
initrd          /initrd.img-2.6.22-14-generic

If you want to use vga modes - [http://ubuntuforums.org/showthread.php?t=577457](http://ubuntuforums.org/showthread.php?t=577457) - this thread might be helpful.

---

### Post by movrshakr on 2007-12-20
Thanks, I'll try that.

LATER:  It works.  The screen resolution at that point in the process is very low, so the characters are large and lines are longer than screen width, but it did eliminate the splash screen.

---

