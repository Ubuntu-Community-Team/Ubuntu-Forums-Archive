---
title: "Backup MBR to USB drive"
date: 2009-03-03
forum: General Help
---

### Post by 1ronlung on 2009-03-03
Hi.

In the past I've managed to wreck my MBR and/or Grub on about 3 occasions.
I've just installed a dual boot system and it's time to get proactive ;)

I've meandered across software I've got that will let you backup/restore MBR to floppy, but I have no drive.  Can someone recommend something reliable to backup/restore to USB ?

Thanks in advance.

---

### Post by x33a on 2009-03-03
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

> Back up the MBR 
dd if=/dev/hda of=/home/hda.boot.mbr bs=512 count=1

Restore MBR (from a Live CD) 
dd if=/mnt/hda1/home/hda.boot.mbr of=/dev/hda bs=512 count=1

try

```

dd if=/dev/hda of=/media/disk/hda.boot.mbr bs=512 count=1
```

here /media/disk = location of the usb drive.

---

### Post by 1ronlung on 2009-03-03
Thanks for the answer, dude.  I'm suitably embarassed that my question was covered in a FAQ ;)

Unfortunately, I'm still very much a linux newbie and as such, am still scared of the command line:confused:

Anyone know of a user friendly GUI type app to do this ?  I have read the FAQ and they were unable to suggest one ...

Thanks again.

---

### Post by x33a on 2009-03-03
though the command line option is really easy, but you can try quickstart.

[http://www.ubuntugeek.com/quickstart-back-up-restore-and-set-up-ubuntu-quickly-and-easily.html](http://www.ubuntugeek.com/quickstart-back-up-restore-and-set-up-ubuntu-quickly-and-easily.html)

i haven' tried it myself though.

---

### Post by 1ronlung on 2009-03-03
Just been playing with it.  Seems to do the job, ok.
Only downer is that you need to have the software installed to recover data.
The install script includes a wget, which is no use to me off a live CD as I've got a broadcom n/work card.
I think I've d/l'ed all files I need through.

Thanks for pointing me in the right direction :)

---

