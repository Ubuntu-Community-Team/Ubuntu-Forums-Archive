---
title: "Major Help Needed!"
date: 2006-01-11
forum: Desktop Environments
---

### Post by Grimlock on 2006-01-11
I have lost a lot of files from my fat32 partition. I have no idea how this has happened. Iwas deleting a few rar files I did not need and the next thing i know I have basically nothing left!!! Can anyone help me as they are not in the trash can

---

### Post by Thirsteh on 2006-01-11
If they're not in your normal user's Trash folder or /root/.Trash (view as root), then they're either in whatever location you moved them to, or if you didn't move them, they're gone. Try 'sudo ls /root/.Trash' though.

---

### Post by az on 2006-01-11
[http://foremost.sourceforge.net/](http://foremost.sourceforge.net/)

Unmount the partition and run this on the device.  It will spit out the files it can recover (undelete)

If your partition was small enough, you should image it and run things on the image instead.

---

### Post by Grimlock on 2006-01-13
I tried foremost and it gave me a headache lol. I eneded up using a windows tool. Cheers for the help though.

---

