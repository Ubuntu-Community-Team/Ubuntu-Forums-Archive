---
title: "Missing FS in Computer:///"
date: 2005-11-10
forum: Desktop Environments
---

### Post by SilentGreg on 2005-11-10
Hey everyone,

I just noticed something in "Computer." My Shared Data mount does not appear in there but the partition is mounted and accessible. I can read and write (fat32) without a problem but there is no short mount point in computer:///... Any ideas?

Greg

---

### Post by earobinson on 2005-11-10
mount it in the /media dir instead of the /mnt

---

### Post by SilentGreg on 2005-11-10
[QUOTE=earobinson]mount it in the /media dir instead of the /mnt[/QUOTE]

I shall try that. However, I have three Samba mounts that are mounted from a share on the same computer. Their mount point resides in /mnt. :confused: 

Greg

---

### Post by SilentGreg on 2005-11-10
No dice.

Here is my fstab.

> 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc            /proc           proc    defaults        0       0
/dev/sda5       /               reiserfs notail          0       1
/dev/sda6       /home           reiserfs defaults        0       2
/dev/sda7       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdd        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0

/dev/sda3	/media/Data	vfat	defaults,umask=000	0	0

//GMAC03/Music         /mnt/gmac03/Music     smbfs     username=SharedFiles,password=~~~~,ip=172.20.174.14     0     0
//GMAC03/Pictures      /mnt/gmac03/Pictures     smbfs  username=SharedFiles,password=~~~~,ip=172.20.174.14     0     0
//GMAC03/Unsorted      /mnt/gmac03/Unsorted     smbfs  dmask=777,fmask=777,username=SharedFiles,password=~~~~,ip=172.20.174.14     0     0


---

### Post by earobinson on 2005-11-11
Hum, it worked for me at home
(Im lost for ideas, ill do some googling and try and get back to you)

---

### Post by SilentGreg on 2005-11-14
Thanks!


Anyone else have any other ideas? :???:

---

