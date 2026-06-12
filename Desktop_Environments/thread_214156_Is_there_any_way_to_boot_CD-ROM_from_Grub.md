---
title: "Is there any way to boot CD-ROM from Grub?"
date: 2006-07-12
forum: Desktop Environments
---

### Post by Najand on 2006-07-12
I want to add an option to Grub Bootloader for booting  the CD-ROM. I have a dual bootloader (Windows, Ubuntu, Mac for Intel) and it would be  very nice if I  could boot a CD-ROM from Grub (My system does not boot CDROM first automatically and everytime I have to change the Bios setting (Impossible to change the boot order permenantly). I would appreciate any replies.:-k

---

### Post by Paerez on 2006-07-12
try adding this to /boot/grub/menu.lst:
```
title cdrom
  root (hd1)  # if your cdrom is hdb, which it probably is
  chainloader +1
```

---

### Post by GrahamPR on 2007-01-02
> **Paerez said:**
> try adding this to /boot/grub/menu.lst:
```
title cdrom
  root (hd1)  # if your cdrom is hdb, which it probably is
  chainloader +1
```

ok, just before  do this, is my dvd rom drive hdc? I have two physical hard drive, each with several partitions. a dvd drive and a cdr drive.

---

### Post by Dies on 2007-01-02
[http://gentoo-wiki.com/TIP_Chainloading_a_bootable_CD-ROM_from_GRUB](http://gentoo-wiki.com/TIP_Chainloading_a_bootable_CD-ROM_from_GRUB)

---

### Post by GrahamPR on 2007-01-03
thanks for the link. :)  can't seem to download the memdisk and sbm file though. :( 

any other ideas?

---

### Post by Rhubarb on 2007-01-03
Try upgrading your BIOS firmware, go to your motherboard manufacturer's website and check if there's any updates.

If you notice the computer can't remember what time and date it is, then you've got a flat battery on your motherboard.  This can explain why it can't remember the boot priority every time you do a cold boot.
There's a good chance the on-board battery is a standard button cell CR-2032.

---

### Post by GrahamPR on 2007-01-03
bios is fine. updated to the latest version possible last year. time and date are fine.

just need the text to edit the menu.lst (and maybe device.map?) to get a cdrom option. :( 

is my cdrom hdc?

---

### Post by Malac on 2007-01-03
> **GrahamPR said:**
> is my cdrom hdc?

If you have two hard disks then, yes, /dev/hdc, which is (hd2,0) in GRUB, should be your dvd/cdrom.

---

### Post by GrahamPR on 2007-01-03
ok.. I added this to menu.lst

title cdrom
root (hd2,0)
savedefault
makeactive
chainloader +1

and added this to device.map

(hd2) /dev/hdc

.. I got the option on the grub menu, but when selected it says "device does not exist".

---

### Post by GrahamPR on 2007-01-03
do I need to add a "mount" command in there somewhere?

---

### Post by Paerez on 2007-01-03
type:
```
grep cdrom /etc/fstab
```
while ubuntu is running to find out what your cdrom is.

/dev/hda -> hd(0)
/dev/hdb -> hd(1)
/dev/hdc -> hd(2)
etc...

then use what I posted earlier.

---

### Post by GrahamPR on 2007-01-04
sorry mate, no joy.

Got:

Error 21 selected device does not exist. ](*,)

---

### Post by Paerez on 2007-01-04
you are doing hd(2) not hd(2,0) right? It should be hd(2)

---

### Post by Dies on 2007-01-04
AFAIK GRUB does not yet support this so no matter what you add to the menu it won't work right and that's why that tutorial exists not because they just felt like doing it the hard way, maybe in a future version.

Anyways I attached the files, good luck.

---

### Post by GrahamPR on 2007-01-05
> **Paerez said:**
> you are doing hd(2) not hd(2,0) right? It should be hd(2)

Yup, just checked again to be sure ;)

Thanks for the info Dies. I'm not giving up yet. :D

---

### Post by Paerez on 2007-01-05
Pretty sure dies is right on this one. Here is the same tutorial he referenced, but on another site:
[http://cutecomputer.wordpress.com/2006/10/10/boot-cdrom-through-grub/](http://cutecomputer.wordpress.com/2006/10/10/boot-cdrom-through-grub/)

I must have found some other reference to it on another forum that was also incorrect.

---

### Post by stelloscuro on 2007-01-26
Thanks guys this sorted my thinkpad out:guitar:

---

