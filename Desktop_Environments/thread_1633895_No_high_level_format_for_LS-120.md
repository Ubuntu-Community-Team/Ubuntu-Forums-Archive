---
title: "No high level format for LS-120"
date: 2010-11-29
forum: Desktop Environments
---

### Post by yyyc186 on 2010-11-29
I'm running 10.10, but this seems to be an ongoing problem.  While every other OS on the planet seems to be able to high level format LS-120 super floppies in their IDE drive, Linux can't.  DR DOS can.  OS/2 can.  Windows 98 forward can.

We aren't talking low level format here.  We are talking "quick" format where a new FAT and label are written to the media along with the high level markings/surface scan.

I can load a disk, copy to it, delete from it, but cannot perform a high level format.

---

### Post by yyyc186 on 2011-02-14
It appears FreeBSD addressed this issue back in 1998 or so?  How come it hasn't bubbled out to others?

[http://configure.sh/FreeBSD/ls120.html](http://configure.sh/FreeBSD/ls120.html)

---

### Post by inobe on 2011-02-14
it being discontinued might not have nothing to do with it?

---

### Post by matt_symes on 2011-02-14
Hi

I have never used an LS-120 so this may be totally incorrect but can you not format it with 

```
mkdosfs
```

or one of the other variants (mkfs.vfat) ?

Kind regards

---

