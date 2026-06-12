---
title: "Can't read from an NTFS partition."
date: 2005-10-26
forum: Desktop Environments
---

### Post by StrikeRTM on 2005-10-26
I have 3 mounted partitions -- 2 NTFS and 1 FAT32...+Linux partition and swap of course.

I can't open the NFTS partitions. I'm getting this error:

==============================================
You do not have the permissions necessary to view the contents of "hda5".
==============================================

This is my FSTAB:
==============================================
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda4       /               reiserfs notail          0       1
/dev/hda1       /media/hda1     ntfs    defaults        0       0
/dev/hda5       /media/hda5     ntfs    defaults        0       0
/dev/hda6       /media/hda6     vfat    defaults        0       0
/dev/hda3       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
==============================================

I've no idea what might be wrong...or where. Any suggestions or ideas how to get to that partition...to both of them?

---

### Post by hajk on 2005-10-26
My /etc/fstab entry for an NTFS partition has the options "ro,noauto,users,umask=0222" for the following reasons:

ro -- read only, because writing in Linux to an NTFS is dicey...
noauto -- because I don't access an NTFS that often, now it only appears 
              on the desktop when I click on it in Places/Computer
users -- so that users can mount it (and not sudo)
umask=0222 -- this one solves the permissions problem in your post.

---

### Post by StrikeRTM on 2005-10-26
How excatly does your fstab file look like? I've never before edited it, had no need, but now I dont know to which line I should add that.

---

### Post by manicka on 2005-10-26
run 

sudo gedit /etc/fstab

change this

/dev/hda5       /media/hda5     ntfs    defaults        0       0

to this

/dev/hda5       /media/hda5     ntfs     defaults,umask=002,nls=utf8 0 0

---

