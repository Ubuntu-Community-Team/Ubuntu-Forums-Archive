---
title: "rsync strange bahaviour"
date: 2009-04-18
forum: General Help
---

### Post by Gingalone on 2009-04-18
I use this rsync command to backup files on a USB HD:
code
rsync -Havu --delete /home/mydir /media/usbhd1

but in my home dir there are files which names are all capital letters (e.g. GINO.TXT) and rsync copies these files to the USB HD writing the names in small letters (e.g. gino.txt) and when I run that rsync command again, it takes those files as non existent in the source dir (because their name is different there!) so deletes the files and then copies them again but, again, writing their names in small letters....
Of course the files have not been modified in the meantime!
In man rsync I can't find anything about capital letters in filenames ... 
What about???
Thanks for any illumination!
Gingalone

---

### Post by unutbu on 2009-04-18
Please post the output of 
```

df -T /home/mydir 
df -T /media/usbhd1
```

This will show us the filesystem type of the filesystems containing mydir and usbhd1.

---

### Post by Gingalone on 2009-04-19
> **unutbu said:**
> Please post the output of 
```

df -T /home/mydir 
df -T /media/usbhd1
```

This will show us the filesystem type of the filesystems containing mydir and usbhd1.

Filesystem    Type   1K-blocks      Used Available Use% Mounted on
/dev/sda5     ext3   226036040  45823640 168730348  22% /

/media/SD1    vfat     1570548    917212    653336  59% 

(actually the usb unit with which I have that rsync problem is a SD card)

Thank you,
 Gingalone

---

### Post by unutbu on 2009-04-19
Please post the output of 
```

mount
```

---

### Post by Gingalone on 2009-04-19
> **unutbu said:**
> Please post the output of 
```

mount
```

/dev/sda5 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-11-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ginus/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ginus)
/dev/sdb1 on /media/SD4Gb type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)

Thank you for attention,
Gingalone

---

### Post by unutbu on 2009-04-19
The mount point keeps changing. Is the output you've posted for /media/SD4Gb, /media/SD1, and /media/usbhd1 all referring to the same device?

---

### Post by Gingalone on 2009-04-20
> **unutbu said:**
> The mount point keeps changing. Is the output you've posted for /media/SD4Gb, /media/SD1, and /media/usbhd1 all referring to the same device?

yes, I am sorry, I changed the name of the SD card and forgot to change it in the post...

Gingalone

---

### Post by kpkeerthi on 2009-04-20
When syncing linux partitions with FAT32, I'd use --modify-window=1 to compensate for the difference in the way the timestamps are handled in FAT32.

```

rsync -Havu --modify-window=1 --delete /home/mydir /media/usbhd1

```

---

### Post by Gingalone on 2009-04-29
> **kpkeerthi said:**
> When syncing linux partitions with FAT32, I'd use --modify-window=1 to compensate for the difference in the way the timestamps are handled in FAT32.

```

rsync -Havu --modify-window=1 --delete /home/mydir /media/usbhd1

```

I tried it, but no work... It is not a problem of time synchronisation, it's just an inexplicable mess between capital and small letters....!

Gingalone

---

### Post by kpkeerthi on 2009-04-29
I sync my FAT32 iPod running rockbox just fine with that command. Although the folder and file name cases are mixed it works fine for me.

---

### Post by Kareeser on 2009-04-29
I'm guessing the switch "H" and "a" conflict. Try without "H", do you really need to preserve your hard links?

---

