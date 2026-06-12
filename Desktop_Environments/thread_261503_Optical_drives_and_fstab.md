---
title: "Optical drives and fstab"
date: 2006-09-20
forum: Desktop Environments
---

### Post by martal on 2006-09-20
Nautilus can't see my optical drives (a cd-rw, a dvd-ro and a usb external dvd burner). SoundJuicer can play from all of them.

/etc/fstab is:

/dev/hdc /media/cdrw udf iso9660,users,noauto,rw 0 0 #the first
/dev/hdd /media/dvdro udf iso9660,users,noauto,ro 0 0 #the second
/dev/hde /media/dvdrw udf iso9660,users,noauto,rw 0 0 #the third

Errors in Nautilus:
"cdda:///dev/hdc" is not a valid location. for the first
"cdda:///dev/hdd" is not a valid location. for the second
"cdda:///dev/scd0" is not a valid location. for the third ???

I'm doing something wrong in fstab.

---

### Post by kick6 on 2006-09-20
try accessing the directory /media/cdrw

---

### Post by martal on 2006-09-20
It shows empty.

---

### Post by kick6 on 2006-09-20
do you have an icon for any of the discs on your desktop?

---

### Post by martal on 2006-09-20
I've turned on volumes_visible, put audio cd in all three, and yes, I have three icons on the dektop.

---

### Post by martal on 2006-09-20
What would the default values for these three drives be in /etc/fstab ?

---

### Post by staceyb68 on 2007-12-02
I'm having the same problem as martal.

CD/DVD Burner can't see my optical drives a cdrw(hdc) cdrom (hdd). SoundJuicer can play from them.

/etc/fstab is:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=3c38d16e-ca4b-4703-bbe7-c08495a8e595 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=81319027-586c-4aab-a548-16ecd9ca7e51 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

/dev/hdc is cd/rw
/dev/hdd is cdrom


I put a  store-bought cd in both drives (one at a time):
Sound Juicer will play from both
Audio disk icon shows up in desktop for both
Errors in CD/DVD Creator:
"cdda:///dev/hdc" is not a valid location
"cdda:///dev/hdd" is not a valid location
in directory /media/cdrom0 shows blank
in directory /media/cdrom1 shows blank

I don't know how to find the default values for this drive in /etc/fstab.

Will someone please help me straighten out this drive issue?  Thanks.

---

