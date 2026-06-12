---
title: "Multiple kernels? Multiple OSes? Help!"
date: 2009-02-01
forum: General Help
---

### Post by vegetarianshrimp on 2009-02-01
(Staff: I didn't know where to put this thread, so please feel free to move it)

Hi. I've noticed that when I go to the grub menu (when starting up my Dell Inspiron Mini 9 with Ubuntu 8.10 installed via LiveUSB made with UNetbootin) There are multiple "Ubuntu 8.10"s. This is what there is:

> 
Ubuntu 8.10, kernel 2.6.27-11-generic
Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
Ubuntu 8.10, kernel 2.6.27-9-generic
Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
Ubuntu 8.10, kernel 2.6.27-7-generic
Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
Ubuntu 8.10, memtest86+I understand the recovery mode and the memtest86+ (even though I don't really know what that is), But what I don't get is having 7. 9. and 11 at the end of the kernel number.
Actually, it used to be only 7 and 9, but now its also 11....:confused:

---

### Post by taurus on 2009-02-01
That is not a multiple OSes.  It just means you have three different kernel versions.  Each time there is a kernel update, it will create two more entries in /boot/grub/menu.lst, one for normal boot and one for recovery mode.  So you can use synaptic to remove the old ones if you wish but you should consider leaving at least one old one in case the new one is having problems.

---

### Post by vegetarianshrimp on 2009-02-01
oooooooooooh....I get it now, thanks.

---

### Post by taurus on 2009-02-01
If you want to remove the recovery mode entries and the memtest from GRUB menu, you have to edit /boot/grub/menu.lst.

```
gksudo gedit /boot/grub/menu.lst
```
But if you want to remove the kernel, than it's easiest to do it from synaptic.  Just use the Search button for the search and delete the right version.

---

### Post by vegetarianshrimp on 2009-02-01
So which ones would you recommend leaving, and which ones deleting?

---

### Post by taurus on 2009-02-01
I would leave the 11 & 9 and remove the 7.

---

### Post by vegetarianshrimp on 2009-02-01
Ok, thanks.

---

