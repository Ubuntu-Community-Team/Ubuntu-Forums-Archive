---
title: "Mount NTFS: Permissions Problem"
date: 2006-10-07
forum: Desktop Environments
---

### Post by dave2010 on 2006-10-07
Hi,
I installed an 80gig Hdd full of mp3s, i can see it in administration->discs, it says partiton5 ntfs, mount point /media/MP3.
When i try and access t in nautilus it tells me thats its a read-only file system.
my fstab entry;

/dev/hdb5 /media/MP3      ntfs-3g    silent defaults,locale=en_GB.utf8 0 0 

so far i have tried chowning and chmodding both /dev/hdb5 and /media/MP3 (tried to make this 777)
and nothing, stll says its a read-only filesystem.
I KNOW that, i dont need to write, i just need it to mount and be able to read!
It comes up when i issue "mount" as /dev/hdb5 /media/MP3 ntfs-3g    silent defaults,locale=en_GB.utf8 0 0 

my ntfs-3g works fine, i was accessing my windows partition til yesterday wheni finally deleted it.
Help please!
I have a feeling it may well be something to do with the fact that i compressed the drive when i was still using XP.
Thanks,
Dave

---

### Post by lemonsCC on 2006-10-07
oops didnt read it all

---

### Post by dave2010 on 2006-10-07
Super helpful, thanks.

---

### Post by lemonsCC on 2006-10-07
I couldn't delete the post so I editted it.

A little googling and i came across this...let us know what happens

[How_to_mount]("http://ubuntuguide.org/wiki/Dapper#How_to_mount.2Funmount_Windows_partitions_.28NTFS.29_manually.2C_and_allow_all_users_to_read_only")

---

### Post by dave2010 on 2006-10-07
Ah cheers mate, i had read that before whilst searching around.
the mount commands make it all good but i still cant get my fstab riight.
Too much beer to mess with filesystem,s now, adios.

---

