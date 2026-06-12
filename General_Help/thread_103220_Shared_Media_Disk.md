---
title: "Shared Media Disk?"
date: 2005-12-13
forum: General Help
---

### Post by matthinckley on 2005-12-13
OK I think my title was a little cryptic but I couldn't think how to word my problem exactly..

Here's what I've got

hda1 mounted as /
hda3 mounted as /home
hda4 mounted as /storage

my /storage drive has all of my pictures and music and movies on it

my problem is that my wife and I both use this computer and we both put pictures from our cameras in the /storage drive.. but we both want to be able to access them.. the /storage drive and subdirectories all have their permissions set to 777 but whenever one of us puts new pictures or anything on the computer it defaults to 700 which doesn't let me look at anything my wife put on the computer and vice versa...

Is there a way to set this directory so any new files stored on it have permissions set to 777 instead of 700?

thanks

Matt

---

### Post by eXidos on 2005-12-13
can you please post your fstab file

---

### Post by matthinckley on 2005-12-13
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc               /proc                proc    defaults        0       0
/dev/hda1       /                      ext3    defaults,errors=remount-ro 0       1
/dev/hda3       /home               ext3    defaults        0       2
/dev/hda4       /storage            ext3    defaults        0       2
/dev/hda5       none                 swap    sw              0       0
/dev/hdc         /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd         /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0         /media/floppy0   auto    rw,user,noauto  0       0
~

---

### Post by matthinckley on 2005-12-14
^^

---

