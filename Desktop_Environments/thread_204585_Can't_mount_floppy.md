---
title: "Can't mount floppy"
date: 2006-06-27
forum: Desktop Environments
---

### Post by ajgreeny on 2006-06-27
Help please.

I've looked around these forums to see how I can mount my floppy drive when I want to but so far with no luck.

My fstab is here:-
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0	/media/floppy0	vfat	rw,user,noauto	0	0

Though I've tried all the possible different file type entries where it says vfat for the floppy file type.

I have tried manual mounting with no luck using:-
sudo mount /dev/fd0 /media/floppy0 -t auto
If I try auto it tells me I must specify file type,
If I try vfat it says wrong file type and that is the same for ext2, ext3, msdos, and everything else I could think of.

Anyone help me please.  The fstab entry is the same as it was for breezy and it all worked there without problems.

OK It's now three hours later and after a lunchtime restart I've found that it seems to be working.  I've changed the file type in my fstab back to auto, as it was in breezy and all seems to be OK now.  I suspect the problem may be linked to the fact that I had a Gag bootdisk in the drive and for some reason, if that is there, it seems that mounting is not possible, with the error message now saying that mount can not determine file type and none was specified.  Anyone know if this is just a Gag thing or have I got some strange happenings going on?

---

