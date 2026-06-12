---
title: "Couldn't find ext2 superblock,"
date: 2006-09-03
forum: Desktop Environments
---

### Post by mikq on 2006-09-03
Hello all new to ubuntu, I recently had an error bootin my system, it got through it, have booted since many times and on the force check it came up with a few errors but coninued on, did a little more research and used a live cd and ran fsck heres the message I got

[I]fsck 1.38 (30-Jun-2005)
e2fsck 1.38 (30-Jun-2005)
Couldn't find ext2 superblock, trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /dev/hda

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>[/I]

when I installed ubuntu i used the entire disk, I spent a lot of time on this version to scratch it and start over anybody, have any idea what I can do to fix this without having to start all over
Much thanx

---

### Post by croak77 on 2006-09-03
Where you running fsck /dev/hda?. It looks like you should fsck on a partition like /dev/hda2 or /dev/hda1 not /dev/hda. Do you know your partition scheme?

---

### Post by mikq on 2006-09-05
Thats what it was, sorry it took so long to get back,
I really appreciate the help'

---

