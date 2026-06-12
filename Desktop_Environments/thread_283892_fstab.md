---
title: "fstab"
date: 2006-10-24
forum: Desktop Environments
---

### Post by jabb0 on 2006-10-24
hello,

I wish to have a seperate partition, which is currently formatted to fat32, on which i can store my music an someother files which will then be accessible to both my windows and ubuntu.

I can go look in the /media/Library folder, but i cannot create a folder in it.

I have done this before and if i remember correctly a icon appeared on my desktop representing this partition, this aint happening wither. plz help.

my fstab
```
proc            /proc           proc    defaults        0       0
/dev/hda5       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda6       /home           ext3    defaults        0       2
/dev/hda1       /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/hda8       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda7       /media/Library  vfat    rw,auto,user         0       0
```The line to which i am referring is the last one.

can u help me make this partition readable?

---

### Post by DaveBorealis on 2006-10-24
> **jabb0 said:**
> 
I can go look in the /media/Library folder, but i cannot create a folder in it.


Open a terminal, type 'cd /media' to get into that directory, and type 'ls -l' to see the permissions for 'Library'.  If it's not 777, which means anyone can write to it, then type 'sudo chmod 777 /media/Library', and I think that might solve your problem.

Best regards,
Dave

---

### Post by taurus on 2006-10-24
Why don't you modify your /etc/fstab and make the last line to look something like this?

```
/dev/hda7       /media/Library  vfat    defaults,umask=0000       0       0
```

---

