---
title: "Complete Backup (Image) of a running root partition"
date: 2009-02-09
forum: General Help
---

### Post by stronzo on 2009-02-09
hello.
i hope somebody can help me. i want to make an complete backup (image) of my ubuntu 8.04 machine in order to restore a full working system in case the hardware crashes. 
the problem is: i can not shutdown the machine for this, because it is acting as a server. so i need a way to get a working image of my running system. i know that most solutions require an unmounted partition but this is not possible for me. i tried partimage, it has an option to save mounted filesystems, but i cant find a documentation what will happen and if it is consistent in the end. maybe someone has some knowledge about using dd or partimage on running partitions?

so if anyone has an idea how i can get a complete backup of my running pc, please tell me how.
thanks a lot :-)

---

### Post by grndslm on 2009-02-09
remastersys if the entire compressed system is less than 4 GB.  That's such a great program!

---

### Post by stronzo on 2009-02-09
very nice program indeed!
the problem is, my root partition contains approx. 40gb and i need them all.
is there absolutely no way to use remastersys for larger partitions?

---

### Post by grndslm on 2009-02-09
Only way you could use remastersys is with the dist version, which excludes your /home folder, which should be where most of that 40 GB is located, unless you got a massive database on there or something.

That's what I've been using remastersys for is the dist version, and my 4 GB installed system only takes up about 1.8 GB on a LiveDVD customized just the way I want it... and I can hand it out to anybody I know, and all they'll have to fill out is their partitioning scheme, their username, & their password... and they'll have a 100% fully operational OS with no extra work.  Too clean.

If you do have a database, perhaps rsync is good enough?

---

### Post by stronzo on 2009-02-10
the pc is acting as a server, dhcp, pxe etc. rsync is no option for me.
and i need to backup the whole pc, not just a part. so does anyone have some other suggestions?

---

### Post by UbuntuNerd on 2009-02-10
check out this link:
[http://my.opera.com/ubuntunerd1/blog/2009/02/07/h]("http://my.opera.com/ubuntunerd1/blog/2009/02/07/h")
maybe It can help you

---

### Post by stronzo on 2009-02-11
what if i rsync everything that is possible? is it enough to bring back a working system? (that really is stable and complete in the end). if so, is there a howto for complete backup?

---

### Post by blackgr on 2009-02-11
Its impossible to know if your image is 100% working without unmounting it first. The best way and the way most servers use is rsync. To have your system back and working, just rsync all folders in root except these ones.

```

/proc
/lost+found
/mnt
/sys
/media
```

After a crash or something else.. just cp -a back all folders you rsynced and if one of the file you excluded isnt there, just mkdir it. 

Another way and propably the best is when the filesystem itself supports it, Like solaris's zfs which holds snapshots of all files.

---

### Post by stronzo on 2009-02-11
hmm ok, maybe rsync really is an option. but what is with the files that are in use and cant be backed up? i think the system will be back running after a restore, but not really consistent?!!

---

### Post by blackgr on 2009-02-11
Consistancy is an issue you cant avoid. BUt the damage of an unconsistant disk image would be much bigger. For this reason use rsync when server traffic is low.Rsync is pretty fast tool and the combination of these 2 will bring the best result.I suggest every once a month to do a full disk image just to be sure. Or if you really care about consistancy use a versioning file system like ext3-cow which keeps snapshots something like zfs.

---

### Post by stronzo on 2009-02-11
hmm yes, you are right. i will think about switching the filesystem to zfs or even lvm, snapshotting would be nice. otherwise i could write a script which automatically shuts the server down in the night to start an imagebackup. but this would be the most work i think...
thanks for all the answers

---

### Post by blackgr on 2009-02-11
Zfs is only available in solaris systems, which is another story. You can check some free versioning filesystems here -> [http://en.wikipedia.org/wiki/Versioning_file_system](http://en.wikipedia.org/wiki/Versioning_file_system)

---

