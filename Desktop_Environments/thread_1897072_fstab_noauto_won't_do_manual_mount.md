---
title: "fstab noauto won't do manual mount?"
date: 2011-12-18
forum: Desktop Environments
---

### Post by RMOP on 2011-12-18
Ii rather hate airing my dirty laundry like this, but here is it: entries from my fstab, unedited.

My automount entry works fine, and the remaining entries work as far as PREVENTING auto-mounting of the specified ntsf partitions.

PROBLEM: if I try to manually mount the noauto entries, I'm advised, courteously, of course, that this is not possible for reasons which are cryptic to me.

Might some intrepid or at least gracious soul peruse the following lines and tell me WHY the auto-mount DOES work and WHY I can't manually mount the remaining entries using sudo mount?

FWIW: if I try to mount from Disk Utility, I'm advised that only root can accomplish this. If I do a sudo mount command from terminal, 

"sudo mount /dev/sde1
fuse: failed to access mountpoint /Windows/Seagate-USB: No such file or directory

This is basic, I'm sure, but beyond me. Should I be using UUID in my mount command, or is it something else? Yes, I have created the /Windows directory...

Many thanks.

UUID=CA9CC57D9CC56513 /media/NTFS\040Data ntfs-3g,auto,uid=1000,gid=100,dmask=027,fmask=137,locale=en_US.utf8	0	0

UUID=5EFC1609FC15DC59 /Windows/NTFS\040Backup ntfs-3g defaults,noauto,umask=777 0 0

UUID=0EF2C7AAF2C7947D /Windows/System\040Reserved ntfs-3g defaults,noauto,umask=777 0 0

UUID=9214F68414F66A9D /Windows/Windows\040System ntfs-3g defaults,noauto,umask=777 0 0

UUID=EE60E5CA60E5999B /Windows/Z-Drive\040Backup ntfs-3g defaults,noauto,umask=777 0 0

UUID=F252D8E452D8AF1B /Windows/Seagate-USB ntfs-3g defaults,noauto,umask=777 0 0

---

### Post by sudodus on 2011-12-18
I'll try to help ...

Yes, in general, it is safer to use UUID, particularly when the /dev/sd[COLOR=Red]X[/COLOR] may change because of hot swapping. But if you have the correct partition name it should work.

You have created /Windows, but have you created Seagate-USB? Mount will not create it.
```
sudo mkdir /Windows/Seagate-USB   # only once
```

---

### Post by RMOP on 2011-12-18
> **sudodus said:**
> I'll try to help ...

Yes, in general, it is safer to use UUID, particularly when the /dev/sd[COLOR=Red]X[/COLOR] may change because of hot swapping. But if you have the correct partition name it should work.

You have created /Windows, but have you created Seagate-USB? Mount will not create it.
```
sudo mkdir /Windows/Seagate-USB   # only once
```

Thanks. That worked, using /dev/sde1. I knew that the /media mount point created directories on-the-fly for removable drives, but didn't realize that directories had to be created prospectively for mounting elsewhere. Would the same be the case for /mnt? I would guess so...

BTW: how DOES one use UUID for a manual mount from terminal? I tried it w/o success and poking around a bit just now didn't show me a clear path...

---

### Post by sudodus on 2011-12-19
man mount:

```
       -U uuid
              Mount the partition that has  the  specified  uuid.   These  two
              options  require  the file /proc/partitions (present since Linux
              2.1.116) to exist.

```

---

### Post by RMOP on 2011-12-19
> **sudodus said:**
> man mount:

```
       -U uuid
              Mount the partition that has  the  specified  uuid.   These  two
              options  require  the file /proc/partitions (present since Linux
              2.1.116) to exist.

```

Thanks. I'll give it a try when I get to my Ubuntu machine.

---

