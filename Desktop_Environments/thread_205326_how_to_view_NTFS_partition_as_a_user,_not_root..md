---
title: "how to view NTFS partition as a user, not root."
date: 2006-06-28
forum: Desktop Environments
---

### Post by kazuya on 2006-06-28
I am dual-booting windows XP and Ubuntu dapper. I have created two users and eventually a root account so as to be able to access the windows partitions and manage the other user accounts easily.

Now, the wife also has used the Ubuntu and the windows we have not touched for like two months now. My issue now is that, there are some window multimedia and ISO files I am trying to burn to CD or DVD for storage. As root, I can see these files, but I cannot change the file permissions of the folders within that partition {NTFS}

Is this where I need to install captive NTFS to allow me write to the partition. As a user, I cannot even see this partition {sa1} to at least be able to read the datas.

Any ideas?

---

### Post by bartbes on 2006-06-28
You CAN'T write to a NTFS partition, never (at least not for a while). So you can't change rights too....

---

### Post by leech on 2006-06-28
What bartbes meant was that he doesn't know what he's talking about :D

You CAN write to an NTFS partition.  Just not natively.  With captive-ntfs (I didn't have much luck with it myself, and I don't know if there is a way to install it in Ubuntu or not.)  Knoppix uses this.

But you can READ with a normal user just fine.  It has nothing to do with the NTFS permissions themselves, but more with how Ubuntu mounts it.

Edit /etc/fstab as root (or use sudo).  Mine looks like this.

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sdb1       /               ext3    defaults,acl,errors=remount-ro 0       1/dev/sdb2       /home           ext3    defaults,acl        0       2
#/dev/sdc1       /media/External ntfs    defaults        0       0
/dev/sda1       /media/windows  ntfs    defaults,users,uid=1000        0       0/dev/sda5       /media/x64      ext3    defaults        0       0
/dev/sdb3       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
```

The /dev/sda1 line is my windows partition.  I'm still not quite certain why, but when I installed Dapper it worked out of the box.  Others haven't been so lucky.  Hopefully this is much more useful as a reply than the previous one you got.  After modifying /etc/fstab, just use umount to unmount the windows drive (in my example, /dev/sda1) and then run 'sudo mount -a'

Leech

P.S. Edited for clarification.  Man I'm tired.

---

### Post by jgcamp99 on 2006-06-28
Ubuntu can read ntfs just fine, which means you can read and copy those files to a Linux partition to do what you seek to do as root. Then again, you can always use Windows to do what you're after as well. But with Ubuntu, just copy them over and do them from within Ubuntu.

---

### Post by aysiu on 2006-06-28
For full instructions, go here: [http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by kazuya on 2006-06-28
thanks guys . awesome tip all. I seriously applaude your efforts. This is why I am now in Ubuntu.

I shall get this going.

---

