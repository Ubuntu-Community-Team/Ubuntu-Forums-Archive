---
title: "automount problems?"
date: 2006-07-28
forum: Desktop Environments
---

### Post by xolot1 on 2006-07-28
i have an HP pavilion laptop running dapper drake.
my micro cruzer automounted flawlessly up until around yesterday.
if i plugged it in, it would pop up on my desktop, and if i pulled it out, it would disappear (tho this probably wasnt the best way of going around this task).

today the usb drive doesnt automatically mount, and neither will a separate 12gb usb HD.

how might i be able to mount these drives by hand, and/or fix this automount situation.

i realize i havent included very much info about my system, but that is because i am rather clueless as to what to copy/paste.

thanks

---

### Post by brandon moore on 2006-07-28
unplug your devices, then run this command:

modprobe -r ehci_hcd

then see if your devices are recognized

---

### Post by xolot1 on 2006-07-29
thank you, that worked.


now i also have a rather old 12gb usb 1.1 harddrive, formated to fat32 (or so windows says).  this does not mount automatically either, but never has. how might i go around accessing this drive?

thanks

---

