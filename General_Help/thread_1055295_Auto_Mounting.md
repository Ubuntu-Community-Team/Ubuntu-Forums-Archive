---
title: "Auto Mounting"
date: 2009-01-30
forum: General Help
---

### Post by fearful on 2009-01-30
I've been trying to auto mount my Windows partition and it seems to work fine but the permissions is screwing it up, I have to mount on sudo therefore it won't auto mount. Here's my /etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc         defaults                    0  0  
# /dev/sda4
UUID=d26fcd73-d156-489f-a3dd-4f98875970e8  /               ext3         relatime,errors=remount-ro  0  1  
# /dev/sda3
UUID=f95ea340-69ea-42ab-9729-16ed86205cd5  none            swap         sw                          0  0  
/dev/scd0                                  /media/cdrom0   udf,iso9660  user,noauto,exec,utf8       0  0  
# /dev/sda1
/dev/sda1       /media/Windows        ntfs    defaults,umask=007,gid=46,noatime   0       0


Any help much appreciated
Thanks.

---

### Post by drs305 on 2009-01-30
> **fearful said:**
> 
# /dev/sda1
/dev/sda1       /media/Windows        ntfs    defaults,umask=007,gid=46,noatime   0       0


You can add "users" so any user can mount it without "sudo", and you can also add your uid (normally "1000" if you were the first user - check with command "id") to make yourself the owner at the time of mounting:
```

# /dev/sda1
/dev/sda1 /media/Windows ntfs defaults,umask=007,**uid=[COLOR="DarkRed"]1000[/COLOR]**,**users**,gid=46,noatime 0 0

```

Just for clarification: You mentioned it won't automount because of "sudo". Fstab is executed during boot and is run as an administrative task. In other words, it is run as "root" during the boot process. NTFS partition permissions are not supported in the usual manner in linux - whoever mounts the partition owns it. If you add the new entries above you can change owner of the mount point, otherwise the mount point will be owned by root (but writable by users).

---

### Post by fearful on 2009-01-30
Thank you so much that worked perfectly

---

