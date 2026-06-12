---
title: "Ubuntu loosing files while copying them to external HD"
date: 2006-08-03
forum: Desktop Environments
---

### Post by PhoenixG on 2006-08-03
Hello, this is not the first time it happens to me, previously it used to happen on Mepis with KDE desktop. And now it's already happening with Ubuntu Dapper. When i'm transfering many huge files (700 MB each one) to an external USB disk, everything seems to be OK, but when disconnecting the disk and reconnecting later at least one of the transfered files has 0 Kb !!!!! sometime 2 of them. And today something related happened too, i deleted a file, shut down the HD, restarted it and the file was still there !!!!

This is very anoying and never happened under windows ¿Is there any HD soft cache used by Ubuntu while transfering files? If so ¿How can I be sure that all the data has been removed from cache and correctly transfered before disconnecting my external HD? (note that Ubuntu says that the transfer is finished, then i'm not disconeecting too early). I think the same apllies to USB memories.

Thansks in advance

---

### Post by Ramses de Norre on 2006-08-03
Do you unmount or eject the drive before unplugging it?? 
And yes ubuntu can use a software cache, so does windows and both have a system for emptying it (save remove and unmount/eject). Easiest way is right clicking the icon of the drive and selecting unmount or eject (whichever is present).
Make sure not to have for example nautilus windows open from the drive, you'll get an error about busy device then.

---

### Post by h00s on 2006-08-03
Is it possible to turn off this delayed writing/deleting on external hard drive/usb memory stick?

---

