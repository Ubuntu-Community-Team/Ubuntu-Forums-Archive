---
title: "Sansa e280 mount problems"
date: 2009-05-22
forum: General Help
---

### Post by aaron424 on 2009-05-22
I have xubuntu 9.04 and a sansa sandisk e280. My problem is that I cannot mount the sansa in either msc or mtp mode. It only mounts when I plug it in before booting up. Even after that the connection is questionable. Often while it it still plugged in xubuntu says that it was unmounted. I cannot find anything that I do that makes it unmount. By the way, neither the original firmware or Rockbox usb mode (I know it is supposed to be buggy) works. They both do the same thing, never mounting when I plug them in after boot. I finially found a podcatcher ( icepodder) but I can't use it. Please help.

---

### Post by corney91 on 2009-05-23
Yeah mine hasn't worked since I upgraded to jaunty... =/
I found this thread: [http://www.anythingbutipod.com/forum/showthread.php?t=42442]("http://www.anythingbutipod.com/forum/showthread.php?t=42442"), which indicates it's a problem with gphoto but I tried compiling the latest libgphoto and it still doesn't work :(

---

### Post by Keith_Beef on 2009-05-26
Since upgrading to 9.04 my Sansa E280 gets connected using gphoto instead of being shown as an external drive.

```
gphoto2://[usb:001,005]/
```

I can still read files from it and write files to it, but cannot edit files while on the device. This is slowing down development of new themes and WPS files. :(

I tried killing off gvfs-gphoto2-volume-monitor, as advised [here]("http://ubuntuforums.org/showpost.php?p=7205851&postcount=4").

But now the player doesn't even get an icon on the desktop, doesn't show up as being mounted, although it is detected by USB...


```
$ lsusb
Bus 001 Device 007: ID 0781:7420 SanDisk Corp. Sansa E200 series (mtp)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 0fce:d019 Sony Ericsson Mobile Communications AB VDC EGPRS Modem
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 044e:300c Alps Electric Co., Ltd Bluetooth Controller (ALPS/UGPZ6)
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```




K.

---

### Post by PGScooter on 2009-06-11
If you guys still have problems, you might want to check it out here:
[https://bugs.launchpad.net/ubuntu/+source/libgphoto2/+bug/355998](https://bugs.launchpad.net/ubuntu/+source/libgphoto2/+bug/355998)

There is a fix posted, and a ppa that uses that fix. There does not seem to have been extensive testing of the fix though.

---

### Post by inspired on 2009-06-26
> **PGScooter said:**
> If you guys still have problems, you might want to check it out here:
[https://bugs.launchpad.net/ubuntu/+source/libgphoto2/+bug/355998](https://bugs.launchpad.net/ubuntu/+source/libgphoto2/+bug/355998)

There is a fix posted, and a ppa that uses that fix. There does not seem to have been extensive testing of the fix though.
Thanks for posting this info.
Has anyone tried this fix and what was the result? Success?
Cheers,
Jonathan

---

