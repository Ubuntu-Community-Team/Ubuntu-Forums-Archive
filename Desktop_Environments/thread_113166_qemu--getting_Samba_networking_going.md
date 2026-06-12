---
title: "qemu--getting Samba networking going"
date: 2006-01-05
forum: Desktop Environments
---

### Post by dgermann on 2006-01-05
Hi--

Finally, after help here and lots of false starts, got Win95 installed under qemu on Ubuntu 5.10.

So now how do I get it to see the network that I have? It is a samba network, the server being on another box, 192.168.0.200.

I found this howto at [http://lists.gnu.org/archive/html/qemu-devel/2004-09/msg00150.html](http://lists.gnu.org/archive/html/qemu-devel/2004-09/msg00150.html)
which has some interesting clues, but so far I cannot make it go. I suspect there is a config file somewhere that needs some work, but what it is, I don't know.

Anybody out there who has any experience getting this going?

Thanks!

---

### Post by paul cooke on 2006-03-10
[QUOTE=dgermann]Hi--

Finally, after help here and lots of false starts, got Win95 installed under qemu on Ubuntu 5.10.

So now how do I get it to see the network that I have? It is a samba network, the server being on another box, 192.168.0.200.

I found this howto at [http://lists.gnu.org/archive/html/qemu-devel/2004-09/msg00150.html](http://lists.gnu.org/archive/html/qemu-devel/2004-09/msg00150.html)
which has some interesting clues, but so far I cannot make it go. I suspect there is a config file somewhere that needs some work, but what it is, I don't know.

Anybody out there who has any experience getting this going?

Thanks![/QUOTE]

HAS ANYBODY got samba filesharing working between windows running in a QEMU session and Ubuntu yet??? if so could you please pass on the "secret"...

This would be purely local sharing on the one machine mind you.

I'm using the current Qemu (0.8.0) with Kqemu compiled in... win98se runs nice and smoothly on this 2.4 GHz box... I just want to share files and get stuff in and out without having to hook up usb to Qemu and unhook it to let Linux see it again.

It might just be a simple thing of getting the Qemu able to see the Linux machines network (I can access the internet fine from inside Qemu)

---

