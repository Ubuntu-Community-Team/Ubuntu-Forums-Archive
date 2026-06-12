---
title: "Map /home/name folder to Samba network drive"
date: 2011-02-08
forum: Desktop Environments
---

### Post by mickwombat on 2011-02-08
Hi,

I have a samba server setup and working nicely.  I've created some 'bookmarks' for different shares and these mount no problem when I click on them.

What I'd like to do is to map my /home/name folder (in Ubuntu) to be a share on this server, for the files to be available offline and to syncronise when logging on/off.  I've done this with my Windows partition which was really easy and it works well.  When I first linked the 'My Documents' folder to be a share on the server, it synced and then all the files were on the server etc.

Any ideas on how to do this?  I've got fairly good experience at linux and can figure out how to automount etc, but really want to do the above.....in particular syncing and files being available offline.

Thanks

---

### Post by mickwombat on 2011-02-15
Anyone?  I'm sure this is possible.....certainly is in Windows.

---

### Post by psusi on 2011-02-15
The caching files locally so they are available when offline part is not possible.

---

### Post by wormyblackburny on 2011-02-15
I'm not sure what you mean by "offline".... I assume you would be talking about a dual boot machine where you want your home directory in Ubuntu to be a sambashare and be able to access it from within windows when you are booted in windows? Yes it's possible, but to do it right it could get messy. The easy part is adding the [HOME] share to smb.conf, the hard part is mounting your home share to an NTFS filesystem so that windows can read it. We could get into all of the complexities of that or you could go the easier route and just get a program that allows windows to read/mount ext3 partitions like this one [http://www.howtoforge.com/access-linux-partitions-from-windows](http://www.howtoforge.com/access-linux-partitions-from-windows)

Now, were it me personally I would do the hard way because it is the better setup. Basically it would be:
1) Use windows to shrink windows partition and create unallocated space
2) use windows to format the space to NTFS
3) Set your mydocuments to save in that new partition
4) Kick over to Ubuntu and set everything to mount automatically (/etc/fstab or [https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions))
5) Add the [HOME] in samba conf
6) Pray everything works....

---

