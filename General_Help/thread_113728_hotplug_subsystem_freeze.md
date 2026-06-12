---
title: "hotplug subsystem freeze"
date: 2006-01-07
forum: General Help
---

### Post by Jay75 on 2006-01-07
Hello I've ben tying to get ububtu breezy on cisnet amd64 for a few days. I used an iso its loaded and formated on drive. It makes it to hotplug subsystem check and freezes. Memtest86+ says everythings ok. Is there anyway to continue loading system?

---

### Post by towsonu2003 on 2006-01-07
when it freezes, try hitting Ctrl+C

you could pass a nohotplug option to your boot... So if your /boot/grub/menu.list have a default entry similar to this:
```

title Ubuntu, kernel 2.6.12-10-686 
root (hd0,2) 
kernel /boot/vmlinuz-2.6.12-10-686 root=/dev/hda3 ro quiet splash 
initrd /boot/initrd.img-2.6.12-10-686 
savedefault 
boot

```
try changing it to
```

title Ubuntu, kernel 2.6.12-10-686 
root (hd0,2) 
kernel /boot/vmlinuz-2.6.12-10-686 root=/dev/hda3 ro quiet splash **nohotplug** 
initrd /boot/initrd.img-2.6.12-10-686 
savedefault 
boot

```
and reboot

Notes: 
*menu.list is a file that grub uses to boot your computer
*to edit it, ```
sudo cp /boot/grub/menu.list /boot/grub/menu.list.backup
sudo gedit /boot/grub/menu.list
edit, save, and exit
```

---

### Post by Jay75 on 2006-01-07
Thank you cntl c worked. I did get on but have to figure out how to fix graphical interface. I got to a menu and input name and pass word it replied ending /$ not sure still trying to figure this out thanks

---

### Post by towsonu2003 on 2006-01-08
[QUOTE=Jay75]Thank you cntl c worked. I did get on but have to figure out how to fix graphical interface. I got to a menu and input name and pass word it replied ending /$ not sure still trying to figure this out thanks[/QUOTE]
I am understanding from this that you cannot log into gnome or kde (the graphical interface) at all and got dropped to the command line (black windows with white writings)? 
in that command line, type ```
sudo dpkg-reconfigure xserver-xorg
``` and choose whatever it suggests to you... once it is over, try it wth ```
startx
``` if you can now login to gnome, it should be fixed. 
if that does not work, type the reconfigure command above again, but choose vesa for the driver instead of whatever it is suggesting and go with the options it gives you again... try it with startx. 
if you still cannot, look at the output of ```
cat /var/log/Xorg.0.log
``` for errors. You can navigate using Shift+PageUp / Down to read the output... If you can somehow, post the error messages you find here... To find the error messages only, type ```
cat /var/log/Xorg.0.log | grep EE
```

good luck...

do you know what video card you are using? or the specs of the computer?

---

