---
title: "Got a Stray Entry in Places - Cant remove"
date: 2009-02-24
forum: Desktop Environments
---

### Post by mister_p_1998 on 2009-02-24
Ok just done a fresh install of Hardy, two partitions, sda1 (main & home)
and sda3 (storage)

Ive got an item called 200.0 GB Media in places that I cant remove, it says its busy or not mounted. 
I tried remming out the sda3 entry in fstab and rebooting, but the 200 gb entry still cant be removed

Heres my Fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=766d9604-e98f-4075-9f8d-b12868cd1053 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=17bdae76-b4ed-422b-9835-778ec6961844 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/mapper/sda3 /storage ext3 defaults 0 0

Any help would be appreciated.
Steve

---

### Post by ScottHW on 2009-03-29
Bump

I also want to know the answer to this, although I have been searching all over with a variety of different keywords and have found nothing...

---

### Post by mister_p_1998 on 2009-04-03
Ive got two now! put a 1TB drive in and the tird partition comes up as another 600mb partition!
I give up!
Steve

---

