---
title: "Cannot Load MicroPython on RPi Pico"
date: 2023-02-10
forum: Desktop Environments
---

### Post by joelindo on 2023-02-10
Ubuntu 20.04.5 LTS (codename: focal)
Dell Latitude D620

When I drag and drop the uf2 file into the Pico, I get "failed to open directory RPI-RP2, permission denied," and I can't (or don't know how to ) change the permissions for the folder (/media/joe/RPI-RP2) or the file. Please help.

---

### Post by TheFu on 2023-02-12
So, the file system on the target storage matters.  

If it is using a native Linux file system, then you can use 'chown' and 'chmod' to set the permissions.  There are hundreds of tutorials on the internet for learning Unix file permissions. If you plan to use any OS except MS-Windows, then you need to learn Unix permissions, since every other popular OS uses them.

If the file system on the target storage is NOT Linux-based, say one of the MSFT proprietary file systems, then you can only set file and directory permissions, owners, groups through the mount options.  Unfortunately, all files and all directories get the same owner, group, and permissions.  If only 1 userid needs access it isn't hard, something like this:
```

mnt_options="-t vfat -o uid=$USER,gid=$USER,fmask=0113,dmask=0002,nodev,windows_names,nosuid,noatime,async"
sudo mkdir /mnt/1
sudo mount $mnt_options /dev/$DEV /mnt/1
```
will work. You'll need to know the DEV.  For NTFS, there is another option I'd add and obviously the type needs to be modified.  I tried to make the command as complete and easy, but still useful.  It is possible to leave off all the stuff from ",nodev" to the end, if you want a shorter command.  

I know nothing about pico-pi ... the easiest way to get the file system used is with a 'df -Th' command.  On a more feature rich Linux, we have 'lsblk -e 7 -o name,size,type,fstype,mountpoint' ... which experienced users would ensure as a shell alias, so they don't have to type it, ever.

Experienced users would make a shell script, so the option length doesn't matter.  I have one for seldom mounted storage, like the MicroSD storage my cameras use.  For storage that I use all the time, I handle it automatically using autofs, but that's more complicated.

Native Linux file systems are better for this. There is a flash friendly file system, f2fs, which supports all the normal, expected Unix stuff, while still reducing the number of write cycles for flash storage.  The downside is the same as for FAT32 and exFAT - it isn't journaled.  Journaled file systems are amazing, which is why NTFS and nearly all Linux native file systems are journaled.

---

