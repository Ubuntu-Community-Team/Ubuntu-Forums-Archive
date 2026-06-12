---
title: "cd not recognized"
date: 2009-04-06
forum: General Help
---

### Post by knubles on 2009-04-06
I have a problem in that my cd device is not recognized.
My dvd device is fine.
My cd does not appear in fstab, mtab or in /dev.
Any help apprciated.
I am running 8.10.

---

### Post by causeitsme on 2009-04-06
What is the output of 

```
dmesg | grep -i cd | grep -i rom

```

---

### Post by knubles on 2009-04-07
The output to that code is:
> [   57.126153] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVDRAM GSA-4160B A301 PQ: 0 ANSI: 5
[   58.029837] Uniform CD-ROM driver Revision: 3.20
[   58.030087] sr 1:0:0:0: Attached scsi CD-ROM sr0
 Hope this helps.

---

