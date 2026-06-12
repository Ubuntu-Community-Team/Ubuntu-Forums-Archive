---
title: "/etc/fstab Lines are bad..."
date: 2009-01-15
forum: General Help
---

### Post by GCFreak on 2009-01-15
Hi,

I was messing around with my /etc/fstab file so I can get Samba shares from my server up on my Mythbuntu media centre, and now mntent reports that line 8 and line 10 of my /etc/fstab file are bad. I managed to get one of them to mount properly before it did this. I didn't modify all the other lines while doing this. Here is my /etc/fstab file as copied from nano:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=6bc81cb7-628e-4354-987c-4697bae67600 /               ext3    errors=remoun$
# /dev/sda6
UUID=9e85fa91-80df-4116-9a5c-f3bbb05da356 /var/lib        xfs     defaults     $
# /dev/sda5
UUID=19971894-3466-4d30-8283-f2c28d6aa99e none            swap    sw           $
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
//10.1.1.2/Movies /dull/movies smbfs credentials=/home/mythtv/.credentials 0 0
//10.1.1.2/Music /dull/music smbfs credentials=/home/mythtv/.credentials 0 0
//10.1.1.2/Photos /dull/photos smbfs credentials=/home/mythtv/.credentials 0 0
//10.1.1.2/Backup /dull/backup smbfs credentials=/home/mythtv/.credentials 0 0

```

Thanks.

---

### Post by blazemore on 2009-01-15
When you do ```
sudo mount -av
```
What do you get?

Edit: Wait hang on, at the end of line 8 should be 0 1 and at the end of line 10 should be 0 0, have you checked that?
Use cat, not nano.

---

### Post by GCFreak on 2009-01-15
That done the trick, thanks alot. =)

---

### Post by blazemore on 2009-01-15
No problem

---

