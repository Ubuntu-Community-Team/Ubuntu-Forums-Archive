---
title: "floppy drive can't detect diskette"
date: 2009-05-09
forum: General Help
---

### Post by ragtimer on 2009-05-09
My Jaunty seems to access the floppy drive on my desktop OK, but it always reports "no disk in drive" or "drive is empty", even though WIndows has no trouble with the floppy.
 
I'm running Ubuntu 9.05 in a virtual machine under VMware in WinXP. The floppy does not appear in the list of devices that VMware can either take over or leave under WIndows -- maybe that's a clue.
 
/etc/fstab does show the "floppy" line.
sudo modprobe floppy  just returns an empty line.
 
Is this a VMware issue, or what? I'm very impressed with VMware and Ubuntu.
Thanks, Mike K.

---

### Post by mb_webguy on 2009-05-09
Try "sudo modprobe floppy".  If that works, then you need to add "floppy" to the /etc/modules file.

---

### Post by ragtimer on 2009-05-10
> **mb_webguy said:**
> Try "sudo modprobe floppy". If that works, then you need to add "floppy" to the /etc/modules file.
 Thanks.  That command, which I had already tried, jsut returns an empty line -- does that mean it worked or not?  It means no errors, that I know.
 
The diskette is still not detected in the drive.
I'll try working on the /etc/modules file.

---

### Post by rscottdrysdale on 2009-11-23
i am also having trouble with a standard desktop floppy drive in ubuntu.

clicking "places/floppy drive" results in access to the disk (floppy light on), but nothing else happens.

going to "places/compter" and double clicking on "floppy drive" says "no media in drive".

i can make it work manually by adding this line to /etc/fstab:

/dev/fd0 /media/floppy vfat rw,user,noauto 0 0

(i  also added floppy to /etc/modules, but don't know if that's necessary)

and creating the mount point with:

mkdir /media/floppy

then manually mounting/unmounting with:

mount /media/floppy

<floppy icon appears on desktop, i can read/write files on the floppy using the new desktop icon and /media/floppy from a shell>

umount /media/floppy

<floppy icon disappears from desktop>

none of that fixes the problems listed above with respect to the "floppy" stuff in the desktop menus.

so things appear to work at the low level, but the desktop stuff doesn't.  "user friendly," they say.  i think not.

why do i want floppies to work?  a 720K 3.5" disk can be read/written by all my machines - commodore 64 & 128 (6502 *AND* Z80!), commodore amigas (68K), windows, and linux (x86).  and there may be a mac (PowerPC) added to the stable soon...

---

### Post by mhampson on 2010-03-24
I found a simpler solution to a similar problem (not ideal but quick and it works) - try:

sudo nautilus






And why do we want floppies? For the Yamaha PSR-620!
[http://upload.wikimedia.org/wikipedia/commons/c/cc/Yamaha_PSR_620.jpg](http://upload.wikimedia.org/wikipedia/commons/c/cc/Yamaha_PSR_620.jpg)

---

### Post by ron999 on 2010-03-24
> **mhampson said:**
> I found a simpler solution to a similar problem (not ideal but quick and it works) - try:

sudo nautilus


That's cool.:D

Previously I was having to use 
```
mount /dev/fd0
```
and
```
umount /dev/fd0
```

---

