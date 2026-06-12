---
title: "Windows Mobile 2003 and synce"
date: 2009-01-13
forum: General Help
---

### Post by funkydan2 on 2009-01-13
Howdy,

I'm trying to get my HP rx3715, running Windows Mobile 2003 2nd edition, to talk with synce.

I've looked all over the place for help, including the [synce wiki](http://www.synce.org/moin/SynceWithUbuntu) and [TomTheWombat's post](http://ubuntuforums.org/showpost.php?p=6258719&postcount=6/), but still can't don't see the directory listing when running 'synce-pls'

I'm trying to connect using the synce-hal method, and regardless of whether the ipaq module is blacklisted or not, the output of synce-pls is:
```

daniel@vaio-laptop:~$ synce-pls
** Message: Hal reports no devices connected
** Message: Odccm is not running, ignoring
synce-pls: Could not find configuration at path '(Default)'

```

However, the device is reported by dmesg
```

[ 3262.880075] usb 2-1: new full speed USB device using uhci_hcd and address 3
[ 3263.067842] usb 2-1: configuration #2 chosen from 1 choice
[ 3263.075924] ipaq 2-1:2.0: PocketPC PDA converter detected
[ 3263.075947] ipaq: active config #2 != 1 ??
[ 3263.076859] ipaq: probe of 2-1:2.0 failed with error -5

```

The device is also listed by lsusb as
```

Bus 002 Device 003: ID 03f0:1016 Hewlett-Packard Jornada 548 / iPAQ HW6515 Pocket PC

```
(Which is slightly unusual, as it is an HP iPAQ rx3715, but understandable as it probably uses the same USB chip as other devices.)
My understanding, is once HAL picks up this device and its contents are listed by synce-pls, then syncing is itself quite easy.

I'd love any tips that point me in the right direction with this.

Daniel

---

### Post by funkydan2 on 2009-01-14
From doing a bit more research, it appears that the problem is in the ipaq module and that I need to recompile that module with a slight patch (changing one line of code) ([https://sourceforge.net/forum/forum.php?thread_id=1371946&forum_id=96106](https://sourceforge.net/forum/forum.php?thread_id=1371946&forum_id=96106)).

Any help on how to rebuild the ipaq module?

Daniel

(In hardy there was an ipaq-dkms package - [https://launchpad.net/~synce/+archive](https://launchpad.net/~synce/+archive) in a PPA, but I can't see one for intrepid.)

---

