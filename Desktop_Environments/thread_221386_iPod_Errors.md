---
title: "iPod Errors"
date: 2006-07-23
forum: Desktop Environments
---

### Post by Sethro on 2006-07-23
I love to use my iPod alot, and Iam having difficulty understanding the whole mount/unmount iPod thing. Can't Ubuntu automatically do all that stuff, because when I plug in my iPod I get an iPod icon on my desktop. But when I try to use gtkpod or something else I get alot of errors like "Could Not Access..." etc.


Could somebody throw me a link to a guide for noobs.


Thanx.

---

### Post by Sethro on 2006-07-23
Anybody ... Please](*,) ](*,)

---

### Post by mlind on 2006-07-23
Are you using Dapper? 

I don't use gtkpod anymore, but when I plug my ipod on usb, it's automatically mounted and I can play music from it using Rhythmbox or Banshee.

umounting is same for all removable drives. You must umount it before removing the device, so that it has time to write all pending operations to the disk.
If you don't do that, you can corrupt device's memory.

---

### Post by Thund3rstruck on 2006-07-23
I have never had a problem with [Amarok]("http://amarok.kde.org/index.php?full=1&set_albumName=1-2-series&id=sidebar&option=com_gallery&Itemid=60&include=view_photo.php"). After your ipod gets mounted and is visible on the desktop run:

```

$ mount|grep ipod 

```

This will show you where the ipod is being mounted, probably in /media/ipod. You have to tell amarok that its mounted there and you should be good to go

---

