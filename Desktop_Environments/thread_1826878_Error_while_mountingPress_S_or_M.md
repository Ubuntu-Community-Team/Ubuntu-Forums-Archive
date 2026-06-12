---
title: "Error while mounting:Press S or M"
date: 2011-08-17
forum: Desktop Environments
---

### Post by manosone on 2011-08-17
Hello,

Recently i installed ubuntu 10.04 on a system which had windows xp.
After installation i got an error:"Serious Error were found while checking the disk drive for /media/new_disc " "Press I to Ignore, S to Skip Mounting or M for Manual Recovery" 

After some help from greek forum i changed my fstab from this ```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=cb4dcd83-dbd1-46b8-96b2-a03123006610 /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=178f6c05-7952-48b7-b14a-4b98eb079c36 none            swap    sw              0       0
# me to xeri
UUID=6E5CCF385CCEFA3B   /media/new_disc           ntfs   defaults   0   2
```

to this(last lines changed)
```

#/etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=cb4dcd83-dbd1-46b8-96b2-a03123006610 /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=178f6c05-7952-48b7-b14a-4b98eb079c36 none            swap    sw              0       0
# me to xeri
UUID=6E5CCF385CCEFA3B   /media/new_disc           ntfs
rw,auto,users,exec,nls=utf8,umask=003,gid=46,uid=1000    0   2
```

Then i was able to mount the disc but now i got this error "an error occured while mounting 0 press s to skip mounting or m for manual recovery".

Any ideas?

---

### Post by Elfy on 2011-08-17
> UUID=6E5CCF385CCEFA3B   /media/new_disc           ntfs
rw,auto,users,exec,nls=utf8,umask=003,gid=46,uid=1000    0   2

try it as one line

```
UUID=6E5CCF385CCEFA3B   /media/new_disc  ntfs  rw,auto,users,exec,nls=utf8,umask=003,gid=46,uid=1000    0   2
```

Check the syntax here - [https://help.ubuntu.com/community/Fstab#Fstab%20File%20Configuration](https://help.ubuntu.com/community/Fstab#Fstab%20File%20Configuration)

---

### Post by manosone on 2011-08-17
> **forestpiskie said:**
> try it as one line

```
UUID=6E5CCF385CCEFA3B   /media/new_disc  ntfs  rw,auto,users,exec,nls=utf8,umask=003,gid=46,uid=1000    0   2
```

Check the syntax here - [https://help.ubuntu.com/community/Fstab#Fstab%20File%20Configuration](https://help.ubuntu.com/community/Fstab#Fstab%20File%20Configuration)

Unfortunately, when i change it to one line the disk can not be mounted.

---

### Post by Elfy on 2011-08-17
With it on two lines it's not mounting either - when it is on two lines it takes the first line and the second as seperate things. 

Hence the "an error occured while mounting 0" message - it's trying to mount 

rw,auto,users,exec,nls=utf8,umask=003,gid=46,uid=1000 to 0 

Have you looked at the link I gave you? 

Try this 

```
UUID=6E5CCF385CCEFA3B   /media/new_disc ntfs-3g defaults,locale=en_US.utf8 0 0
```

Edit the file save and run ```
sudo mount -a
```

---

### Post by manosone on 2011-08-19
> **forestpiskie said:**
> 

Have you looked at the link I gave you? 



Thanks. Yes i did but the following did worked

Try this 
> **forestpiskie said:**
> 
```
UUID=6E5CCF385CCEFA3B   /media/new_disc ntfs-3g defaults,locale=en_US.utf8 0 0
```

Edit the file save and run ```
sudo mount -a
```

Thanks a lot :)

---

