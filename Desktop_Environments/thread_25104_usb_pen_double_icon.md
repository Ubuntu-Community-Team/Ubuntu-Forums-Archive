---
title: "usb pen double icon"
date: 2005-04-09
forum: Desktop Environments
---

### Post by aledin on 2005-04-09
Hello all,
I have a line like this in /etc/fstab:
/dev/sda1       /media/pen      auto    rw,user,noauto,noatime,sync 0   0
when I plug in the usb pen, two desktop icons appear on the desktop: "Dispositivo rimovibile 131M" (removable device 131M) and "Dispositivo rimovibile 131M (2)", for the same device. One for /dev/sda (unreadable by Nautilus, obviously) and one for /dev/sda1.

On Warty it didn't happened.
Thanks

---

### Post by aledin on 2005-04-09
[QUOTE=aledin]Hello all,
I have a line like this in /etc/fstab:
/dev/sda1       /media/pen      auto    rw,user,noauto,noatime,sync 0   0
when I plug in the usb pen, two desktop icons appear on the desktop: "Dispositivo rimovibile 131M" (removable device 131M) and "Dispositivo rimovibile 131M (2)", for the same device. One for /dev/sda (unreadable by Nautilus, obviously) and one for /dev/sda1.

On Warty it didn't happened.
Thanks[/QUOTE]

Even with the sda1 line in /etc/fstab commented it has the same problem.

---

### Post by aledin on 2005-04-10
[QUOTE=aledin]Even with the sda1 line in /etc/fstab commented it has the same problem.[/QUOTE]

Solution:
It's not fault of Hoary. The pen was formatted as /dev/sda and /dev/sda1 too, soo they appeared in the desktop together.

I deleted /dev/sda1 with cfdisk to solve the problem.

---

### Post by sparks40 on 2005-04-17
I am also experiencing the same problem. When the icon's are clicked, the first one shows "usb disk" and the second one "usb disk-1". I assume that means /dev/sda0 and /dev/sda1. If I try to cfdisk /media/sda, I get an error message which indicates that an unrecoverable error has occured... nothing shows on the cfdisk screen. Could you explain exactly how you accomplished your fix? TNX

---

