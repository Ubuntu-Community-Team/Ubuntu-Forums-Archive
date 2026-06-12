---
title: "ubuntu 8.08 wont boot after installing graphics card"
date: 2008-08-20
forum: Desktop Environments
---

### Post by jpdamigaman on 2008-08-20
HI I wanted to add a graphic card to my dual boot system with xp on it and hardy.

Ubuntu won't boot with this card installed. windows will in safe mode install new driver and it works.

Its a geforce 2 (better than internal graphics)

I'm getting a bigger monitor as old monitor failed

I try to boot recovery mode and most of time it fails too!

but when it dosn't a type startx then it just locks up nothing!

live cds will not work either.

I have linux system rescue cd and I works with no graphical problems!

---

### Post by carolinason on 2008-08-22
it's obviously a driver issue. try sudo dpkg-reconfigure xserver-xorg

boot the Linux system into single user mode to reconfigure
[http://www.cyberciti.biz/faq/grub-boot-into-single-user-mode/](http://www.cyberciti.biz/faq/grub-boot-into-single-user-mode/)

---

### Post by PhaeZee5 on 2008-08-23
What's Ubuntu 8.08?

---

