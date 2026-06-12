---
title: "Broken loopback device"
date: 2006-11-01
forum: Desktop Environments
---

### Post by caliskan on 2006-11-01
I seem to have a problem with the loopback device under Ubuntu 6.06.  I load the "loop" module and see that loopback devices /dev/loop0 to /dev/loop7 have been created.  However, when I try to access a loopback device:

root@acaliskan:/dev# losetup /dev/loop0
/dev/loop0: [a6fc]:8 (&#65533;&#65533;&#65533; 3&#65533;&#65533;&#65533;&#65533;&#65533;d!) offset 134642904, undefined encryption
loop: can't get info on device /dev/loop0: No such device or address

This happens on both two computers that I have Ubuntu 6.06 installed.  Seeing the garbage printed out in the error message makes me think that the loopback device is somehow seriously broken.  Any ideas about this?  Is this normal or is something about my loopback device broken?

---

