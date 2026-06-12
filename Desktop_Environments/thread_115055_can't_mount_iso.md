---
title: "can't mount iso"
date: 2006-01-09
forum: Desktop Environments
---

### Post by akurashy on 2006-01-09
I get a weird error while mounting

david@akulinux:~/$ sudo mount 1.iso /media/iso -t iso9660 -o loop
mount: wrong fs type, bad option, bad superblock on /dev/loop0,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


I don't know what is it :(

---

### Post by soulestream on 2006-01-09
did you look at dmesg | tail


do you have a custom compiled kernel?


soule

---

### Post by akurashy on 2006-01-09
[quote=soulestream]did you look at dmesg | tail


do you have a custom compiled kernel?


soule[/quote]

[4314328.319000] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[4314328.319000] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[4314328.319000] agpgart: Putting AGP V3 device at 0000:02:00.0 into 8x mode
[4314328.604000] agpgart: Found an AGP 3.0 compliant device at 0000:00:00.0.
[4314328.604000] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[4314328.604000] agpgart: Putting AGP V3 device at 0000:02:00.0 into 8x mode
[4327925.616000] Unable to identify CD-ROM format.
[4327930.130000] Unable to identify CD-ROM format.
[4333442.534000] Unable to identify CD-ROM format.
[4333455.551000] Unable to identify CD-ROM format.

---

