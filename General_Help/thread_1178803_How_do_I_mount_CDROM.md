---
title: "How do I mount CDROM?"
date: 2009-06-04
forum: General Help
---

### Post by isgossip on 2009-06-04
hi, i has a question....How do i mount my cdrom?

ken&#65306;2.6.30-020630rc7-generic

```

gedit /etc/fstab

```
fstab content&#65306;
```

proc            /proc           proc    defaults        0       0
UUID=8202fd9d-aeb7-4ef9-bb63-1294b6d10f4b      /                            ext3    relatime,errors=remount-ro 0       1
UUID=1b5e499d-6c26-44f7-8e23-255931c88a8a    /home                  ext3    relatime        0       2
UUID=6f203b03-8779-43e7-9705-168025a722b4    none                    swap  sw              0       0
/dev/scd0                                                                             /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

```

xxx@xxx-laptop:~$ sudo mount -t iso9660 /dev/scd0 /media/cdrom0
mount: &#29305;&#27530;&#35774;&#22791; /dev/scd0 &#19981;&#23384;&#22312; . .................. means : special xxx /dev/scd0 not exists
xxx@xxx-laptop:~$ ls /dev/scd*
ls: &#26080;&#27861;&#35775;&#38382; /dev/scd*: &#27809;&#26377;&#35813;&#25991;&#20214;&#25110;&#30446;&#24405;  means : file or folder  ... not exists

```

```

xxx@xxx-laptop:~$ ls /dev/s*
/dev/sda   /dev/sda5       /dev/sequencer2  /dev/sndstat  /dev/stdout
/dev/sda1  /dev/sda6       /dev/sg0         /dev/stderr
/dev/sda2  /dev/sequencer  /dev/snapshot    /dev/stdin
xxx@xxx-laptop:~$

```

my eng is so poor... thanks

---

### Post by Locutus_of_Borg on 2009-06-04
paste this into a terminal and press enter
```

dmesg|grep CD-ROM

```

post the output here

---

### Post by isgossip on 2009-06-04
Ubuntu version 9.04

xxx@xxx-laptop:~$ dmesg|grep CD
xxx@xxx-laptop:~$ dmesg|grep CD-ROM
xxx@xxx-laptop:~$ 


I can't see anything....

but I can boot from the CD-ROM

Thanks!

---

### Post by Locutus_of_Borg on 2009-06-04
Did you compile the kernel yourself?

It looks like it's missing the necessary modules needed to see your cd unless maybe atapi drives get named something else?

what does
```
lsscsi
```
output?

---

### Post by isgossip on 2009-06-04
hi.Locutus_of_borg

i download the kernel from "http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30-rc7/"
step 1.[linux-headers-2.6.30-020630rc7_2.6.30-020630rc7_all.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.30-rc7/linux-headers-2.6.30-020630rc7_2.6.30-020630rc7_all.deb")
step 2.[linux-headers-2.6.30-020630rc7-generic_2.6.30-020630rc7_i386.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.30-rc7/linux-headers-2.6.30-020630rc7-generic_2.6.30-020630rc7_i386.deb")
step 3.[linux-image-2.6.30-020630rc7-generic_2.6.30-020630rc7_i386.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.30-rc7/linux-image-2.6.30-020630rc7-generic_2.6.30-020630rc7_i386.deb")


i put "lsscisi" in Terminal... it's say

xxx@xxx-laptop:~$ lsscsi
[0:0:0:0]    disk    ATA      FUJITSU MHW2120B 0000  /dev/sda

but the cd-rom hide..yet

---

### Post by isgossip on 2009-06-04
Thanks for your help.

I reboot with "acpi=off noapic". It's working.

why?

---

