---
title: "making exact copy of audi cd"
date: 2005-01-08
forum: General Help
---

### Post by jamaas on 2005-01-08
I'm sure this has been covered but I can't find it.  Is there a package available for making an exact copy of a music cd on ubuntu?  I don't want to compress or convert to mp3, just make a copy.  
TIA

Jim

---

### Post by rider343 on 2005-01-08
I use graveman
gksudo graveman

---

### Post by jamaas on 2005-01-08
Thanks rider,

I've installed graveman but for some reason when I try to run it, it does not seem to find /dev/cdrom, which I think is the device where my cd's are.  Any thoughts?

Thanks

Jim

[QUOTE=rider343]I use graveman
gksudo graveman[/QUOTE]

---

### Post by lee_connell on 2005-01-09
i went into $HOME/.graveman/graveman.conf and changed cdrecord to cdrecord /dev=dev/hdc.

i then rescaned devices and it found it however when i try to create a cd it fails and tells me to make sure i have cdrecord 2 >.  which i do.

?????

---

### Post by jamaas on 2005-01-09
Thanks Lee,

Can anyone else set us both straight on this one?

Jim

[QUOTE=lee_connell]i went into $HOME/.graveman/graveman.conf and changed cdrecord to cdrecord /dev=dev/hdc.

i then rescaned devices and it found it however when i try to create a cd it fails and tells me to make sure i have cdrecord 2 >.  which i do.

?????[/QUOTE]

---

### Post by taygan on 2005-01-12
I replaced the dev=ATAPI:0,0,0 and dev=ATA:0,0,0 with dev=/dev/hda:0,0,0 (in both places) and graveman says the burn was successful but the drive never spun.. (i've got a SATA HD, so my ide cdrw is hda instead of hdc.)

---

### Post by lee_connell on 2005-01-12
Fix to this is to not use graveman because it depends on cdrecord to find your device as does xcdroast and eroaster.

You should use gnomebaker which is a better program anyways and it uses different mechanisms of detecting your recorder and works very well.

---

### Post by wallijonn on 2005-01-12
Graveman:
.graveman/graveman.conf
cdrecord /dev=dev/cdrom

At least it scans & finds 'cdrom' as a device. 

I've had no such luck with gnomebaker, eroaster, groaster,xcdroaster, cdroaster...

---

