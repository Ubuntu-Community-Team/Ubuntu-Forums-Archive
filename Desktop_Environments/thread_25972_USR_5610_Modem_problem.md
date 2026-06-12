---
title: "USR 5610 Modem problem"
date: 2005-04-11
forum: Desktop Environments
---

### Post by Gior on 2005-04-11
I installed KUBUNTU couple days ago. Everithuingis fine exept that my modem USR 5610 is not working. It works fine under other distros (I;m writing under Yoper). All I had to do was to MAKEDEV ttyS4 (it usualy is there) and use it in kppp. (or make link to modem). 
Well it is not working under ubuntu.  :-? 
Any ideas?

PS I tryed other ports with no success and it is NOT winmodem.  [-X (Just in case)

---

### Post by az on 2005-04-11
Install setserial

lspci

sudo setserial /dev/ttyS4 port 0x#### irq # uart 16550A


(you get # from lspci)

---

### Post by Gior on 2005-04-12
Well. that was funny...
I guess setserial is not in default install :roll: ?
I could not find it anyway. Not a big dael if you have another OS, but if not?
I wanna say how should I insatll package from inet repository if my modem is not working without that package?
Well my appologies if I'm mistaken.

---

### Post by az on 2005-04-12
What gets included on the install cd is a subject of lot of discussion.  If no one knows asks, it does not happen.  File a bug report.

Make sure that that is indeed the problem first, by downloading, transfering  and installing setserial first.

---

### Post by jdong on 2005-04-12
Are you telling me that the serial device for your modem is not in /dev? Can you list all the ttyS* devices in /dev?

Can you also post the output of dmesg?

Wrap long posts in [ CODE ] tags to get them in a scrollbar.

---

### Post by Paki on 2005-05-23
This works:

[http://ubuntuforums.org/showthread.php?t=29829](http://ubuntuforums.org/showthread.php?t=29829)

---

