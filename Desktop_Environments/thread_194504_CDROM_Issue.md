---
title: "CDROM Issue?"
date: 2006-06-11
forum: Desktop Environments
---

### Post by Fatjoint on 2006-06-11
When inserting a disc into my CDROM, it mounts the drive and shows the CDROM icon on the desktop, but when I open it there are no contents?

This is a fresh install of Ubuntu, and I've never experienced this problem before in all the Ubuntu distro's I've installed before.  I installed Dapper using this CDROM on this system, so I don't understand how it stop working?

I also noted that if I browse to my mount point, and do a ls -l, I show the contents of the CDROM - but continues to be a problem through the CDROM icon on the Gnome desktop.

Any clues as to what the problem is?

my fstab:

> 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0

/dev/hda1       /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hda5       /media/hda5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1

/dev/hdb1       /boot           ext3    defaults        0       2
/dev/hdb2       none            swap    sw              0       0
/dev/hdb3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb4       /home           ext3    defaults        0       2

/dev/hdc        /media/cdrom0   udf,iso9660,jfs,user,auto     0       0


I tried changing the filetype thinking that may have been the problem, so I added the jfs.

The CDROM is a IDE Creative 52x

---

### Post by elbryan on 2006-06-11
Which model is your CDROM?

---

### Post by Fatjoint on 2006-06-11
[QUOTE=elbryan]Which model is your CDROM?[/QUOTE]

IDE 52x Creative CDROM.

---

### Post by sarhento_lobo on 2006-06-11
My /etc/fstab involving the cd is:

/dev/scd0     /media/cdrom0    udf,iso9660     user,noauto     0     0

You might want to check the "," between the type and options columns. It shouldn't be there (also, I think the "jfs" is invalid).

---

### Post by Fatjoint on 2006-06-11
[QUOTE=sarhento_lobo]My /etc/fstab involving the cd is:

/dev/scd0     /media/cdrom0    udf,iso9660     user,noauto     0     0

You might want to check the "," between the type and options columns. It shouldn't be there (also, I think the "jfs" is invalid).[/QUOTE]


i had added both of those to try and get it to work... so no dice - it works the same before and after.

---

### Post by Fatjoint on 2006-06-13
Just an update to this as I still can't figure out what's going on.

It turns out the CDs I was trying to read can't be read for some reason.  They are the World of Warcraft CDs.  Other CDs, including ones that I have created are read fine.

I still have a general issue with my CDROM however - whenever I put a CD into the drive the CD Icon appears on my desktop as it should, but if I open it, it's blank.

The only way that I can read the contents is if I browse to my /media/cdrom directory.  Is this a dapper bug?

---

