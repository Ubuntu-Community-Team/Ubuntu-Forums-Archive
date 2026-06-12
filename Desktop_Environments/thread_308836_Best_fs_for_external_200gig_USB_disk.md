---
title: "Best fs for external 200gig USB disk"
date: 2006-11-28
forum: Desktop Environments
---

### Post by harisund on 2006-11-28
Hello

I have a 185 Gigabyte drive. It's an external one, and uses USB 2.0 interface to connect to the PC. 

Now, I have used NTSF on it before, and it works. I did lose some space because of the formatting and stuff, but that's fine. 

I want it connected to my Ubuntu box and shared out on the LAN. Of course, Samba is just made for it. 

However, what file system should I use on it? I am not sure if ext2/ext3 would be a very good idea? Of course fat is out of the question. What about ReiserFS or XFS? 

Any suggestions? (And please don't give me just a name. I would like a reason as well :))

---

### Post by JayTee on 2006-11-28
I have a 189GB USB 2.0 external drive. I partitioned it with a 32GB vfat partition so my Windows systems can share and write to it without an add-on utility to write to ext3. I partitioned the rest of the space as ext3 to use as a backup for my /HOME using rsync so I an have backups of all my configs and using partimage I can have a complete backup of my system partition.

---

### Post by harisund on 2006-11-28
An unrelated question, how do you rsync between 2 directories on the same machine?

---

### Post by JayTee on 2006-11-28
Piece of cake! While it's primarily designed to sync over a network connection you can just type rsync /home/"myname"/ /media/backupvol/home/"myname" 
and it'll sync your home directory to the one on the removable media disk.
It works and it's pretty damn fast the first time you run it and even faster with each run since it only writes changed files after the first time.
My external USB 2.0 hard disk ext3 partition is named backupvol and I just used myname as a placeholder for the username. If you arent' the first user on the machine then run it with sudo. Since I'm the only one on here and I have full rights to the external drive I don't need to run sudo to backup to it.
type man rsync for more info on command line examples and options.

---

### Post by dracule on 2006-11-28
I want to re-partition my portable hdd, I lost my gparted livecd and ubuntu wont let my partition it because it is installed on it. but I would do it fat

---

