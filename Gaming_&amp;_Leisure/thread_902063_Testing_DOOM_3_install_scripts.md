---
title: "Testing DOOM 3 install scripts"
date: 2008-08-27
forum: Gaming &amp; Leisure
---

### Post by linuxguymarshall on 2008-08-27
**PLEASE DON´T ASK QUESTIONS. ONLY USE IF YOU KNOW HOW TO**

I just made some scripts to install DOOM 3. I have not tested them so they are most likely unstable. Fell free to try and give feedback

**MAKE SURE YOUR DOOM 3 CDS ARE IN YOUR PRIMARY DRIVE**

BTW, if you are just knowledgeable of shell script and don´t have a copy of DOOM 3 please review it.

---

### Post by linuxguymarshall on 2008-08-27
If anyone wants to help then I need someone to make sure they work then get them in to one install script instead of 4

---

### Post by DoktorSeven on 2008-08-27
Could glue them all together using **read $ENTERKEY** to wait for CD changes, something like (untested):
```

CDROM_DRIVE=/media/cdrom
DEST_PATH=/opt/doom3/ # or wherever
# place download and install binary code here
echo "Insert DOOM 3 disk 1 and press ENTER to continue"
read $ENTERKEY
mount $CDROM_DRIVE
cp $CDROM_DRIVE/Setup/Data/base/pak002.pk4 $DEST_PATH/base/
umount $CDROM_DRIVE

```
and so on for each disk.  Probably good to test for the file not existing at each point as well (wrong CD, didn't insert CD, etc) (**if [ ! -e /path/to/file ]; then *do whatever*; fi**)

---

### Post by Crafty Kisses on 2008-08-27
> **DoktorSeven said:**
> Could glue them all together using **read $ENTERKEY** to wait for CD changes, something like (untested):
```

CDROM_DRIVE=/media/cdrom
DEST_PATH=/opt/doom3/ # or wherever
# place download and install binary code here
echo "Insert DOOM 3 disk 1 and press ENTER to continue"
read $ENTERKEY
mount $CDROM_DRIVE
cp $CDROM_DRIVE/Setup/Data/base/pak002.pk4 $DEST_PATH/base/
umount $CDROM_DRIVE

```
and so on for each disk.  Probably good to test for the file not existing at each point as well (wrong CD, didn't insert CD, etc) (**if [ ! -e /path/to/file ]; then *do whatever*; fi**)

Yeah that's a good idea, nice script though. :)

---

