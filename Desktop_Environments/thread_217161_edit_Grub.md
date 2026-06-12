---
title: "edit Grub"
date: 2006-07-16
forum: Desktop Environments
---

### Post by inf4my on 2006-07-16
when i load up my pc and GRUB loads there are about 4 different instances of ubuntu  so the regular one and the recovery mode listed four different times, then the memtest and then finally my XP. So is there any way i can edit the bootloader to not include those extra instances. Also is there anyway to add a new interface for grub.

---

### Post by reacocard on 2006-07-16
remove the instantces by unistalling the old kernels (search for linux-image in synaptic). i have no idea about how to add a new interface though. it'd be nice, grub as it is a rather boring.

---

### Post by Ocxic on 2006-07-16
edit your /boot/grub/menu.lst  and comment out the recover mode

---

### Post by ayoli on 2006-07-16
you have to edit /boot/grub/menu.lst
```
gksudo gedit /boot/grub/menu.lst
```
then add this below timeout option at begining of the file:
```
## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu
```
this will hide the startup choice.
i think that's better than erase some entries.
regards.

---

### Post by inf4my on 2006-07-16
thanks, a lot of other distros have pretty nice grub boot screens like SUSe and Fedora Core. I found this on a wiki looks promising
[http://doc.gwos.org/index.php/GrubSplash](http://doc.gwos.org/index.php/GrubSplash). That is what makes ubuntu better than others there is so much documentation.

---

