---
title: "HD keeps re-mounting as ReadOnly"
date: 2006-03-03
forum: Desktop Environments
---

### Post by mafro on 2006-03-03
Hey guys,

Ive been getting on sweet with Ubuntu since moving from Debian - I always found Debian to be a bit of pain when it came some stuff.. No such problems here! Except one..

Ive setup TorrentFlux (a php based bit torrent GUI) using the Ubuntu python BitTornado package for the actual downloading.  I have a FAT32 partition of the main drive (hda3), I mount that manually and the BT starts running fine. I come back at some point later and find the HD has re-mounted itself as Readonly. And obviously, my bit torrent has stopped.

I managed to download 75% of 600MB yesterday before it went tits up - no idea whats causing this, and little idea where to start looking.. (Im a relative linux noob)

Any help much appreciated
mafro

---

### Post by akiro.yamamoto on 2006-03-03
If you have a Fat32 partition, your fstab entry should look like this:
/dev/hdb2       /media/data     vfat    user,umask=000        0       0
The important part is the user,umask=000 bit.

---

### Post by riker1968 on 2006-03-03
add rw option in fstab:

/dev/hda[x] /YourMountDir vfat rw,user,auto 0 0

---

### Post by riker1968 on 2006-03-03
or use 

defaults -->  default options that are rw, suid, dev, exec, auto, nouser, and async

/dev/hda[YourNumber] /[PathToMountFolder] vfat defaults 0 0

---

### Post by mafro on 2006-03-04
Ok cheers guys, tried FSTAB but I still have the same problem. Here's my line from the file:

```
/dev/hda3	/media/files	vfat	user,umask=000	0	0
```

A probably related problem is that even when the HD is mounted, I get a "Operation not permitted" when TorrentFlux attempts to chmod() a folder.. Permissions issue? 

But then I create a Link using Nautilus, and attempt to Cut+Paste that onto my mounted drive, I get this:

> ** Message: Hit unexpected error "Operation not permitted" while doing a file operation.

Arrghhh! This is so annoying, the main reason Im using this box is supposed to be BT!!! :confused: 

Any help much appreciated

---

### Post by DavidW2 on 2006-03-04
My guess is that "user" is causing your problem.  You can mount using "defaults" as riker1968 has suggested or mount as I have mounted mine.  (Actually Ubuntu set my mount on install)

/dev/hda5 /media/hda5 vfat rw 0 0

---

