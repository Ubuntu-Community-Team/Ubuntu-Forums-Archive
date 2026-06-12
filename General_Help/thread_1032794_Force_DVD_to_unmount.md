---
title: "Force DVD to unmount?"
date: 2009-01-06
forum: General Help
---

### Post by zami on 2009-01-06
I'm installing a game (Lord of the Rings Online), requiring installing from 2 DVDs.  It's time to put in disk 2, but alas, I can't eject the first disk to enter the second.

I get 
Cannot unmount volume
> An application is preventing the volume 'Disk 1" from being unmounted.

then

> Unable to eject CD-RW/DVD-ROM Drive
DBus error org.freedesktop.DBus.Error.NoReply. Did not receive a reply. Possible causes include :the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

Can I force un-mount?

Can I copy DVD 2 to a hard drive and install from there, next time it asks for disk 2?

-zami

---

### Post by Shazaam on 2009-01-06
Easy way to force eject...
```
sudo eject
```
Somewhere here there are a few posts about multi-disk installs. You might try a forum search (especially in the gaming sub-forum).

---

### Post by zami on 2009-01-06
```
laura@BelleBlue:/media/cdrom0$ sudo eject
umount: /media/cdrom0: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
eject: unmount of `/media/cdrom0' failed

```

Darn! That sounded so promising.

I'll do some searching for better info on multi-disk installs. I know with CDRom games I've been able to just copy the disks to hard drive and install that way, and I've found with most games the "next disk" issue isn't an issue at all.  I was caught a little off guard by this game having this problem since it's installed so smoothly before.

Anyhow, thankee for the help attempt!

-zami

---

### Post by zami on 2009-01-06
If I can't figure this out, I'll take it to the Wine sub-forum since I'm starting to think it's a Wine issue more than a Nautilus or something else issue.  (Still not sure - I freely admit I don't know what I'm doing!)

I'll update here too if I get any answers though.

-zami

---

