---
title: "Problem with Nautilus / XFS"
date: 2006-10-14
forum: Desktop Environments
---

### Post by math on 2006-10-14
When im trying to write a 650mb file to a XFS partition with Nautilus or gnomevfs-copy it takes about 3 minutes. The same procedure with the cp command takes only 15 seconds. I did not have this problem in dapper. Who else uses xfs and can reproduce this?

---

### Post by galactus51 on 2006-10-14
I can and it's even worse! Almost 7 minutes with an iso image of Edgy (693,9MB). 

XFS to Ext3 = 31 seconds!

Ext3 to XFS = almost 7 minutes!

I have noticed that the use of CPU is very low, among 6% when transfering the file ext3 to XFS. On the other hand 4 to 30% of CPU is used when transfering the file XFS to Ext3.

And more, ext3 hard drive is an old IDE with 5400rpm. The XFS hard Drive is a SATA I with 7200rpm.

With the CP commmand:

XFS to ext3 = 22s

ext3 to XFS = 49s

What is going on?

---

### Post by math on 2006-10-15
Is there anyone who uses XFS and has NOT this problem?
That makes XFS almost unuseable. :(
There is already a bug report, but nothing happens :(
[https://launchpad.net/distros/ubuntu/+source/gnome-vfs2/+bug/58672](https://launchpad.net/distros/ubuntu/+source/gnome-vfs2/+bug/58672)

---

### Post by kerry_s on 2006-10-15
I also fine similar problems, so i switched to jfs. Not sure if it's any better but it's been working good for me so far. What i noticed is jfs seems alot more responsive than xfs. Xfs seems to scan(may be buffering) the file first before copying, it has 3 services that run for xfs. Jfs just starts right away and dosen't have that lag. Just my 2 cents.

---

### Post by math on 2006-10-15
I dont know which file system is faster, jfs or xfs, but it is a fact, that with dapper or via terminal xfs is very fast and stable. So the question is if there is someone who uses xfs with edgy without this bug?

---

### Post by shining on 2006-10-15
That's very odd. I'm not using xfs myself (I've no reasons for not using ext3), but I'm very curious about what's going on. I wonder how it's possible, what does nautilus use for copying files ?

---

### Post by math on 2006-10-15
I guess it uses gnomevfs-copy. If i try to use gnomefvs-copy in terminal, i also have these performance problems. So the bug has to be there.

---

### Post by Jenda on 2006-11-01
Thread moved to reopen it.

---

### Post by math on 2006-11-01
Thanks.
The problem still persists. Please look here [https://launchpad.net/distros/ubuntu/+source/gnome-vfs2/+bug/58672](https://launchpad.net/distros/ubuntu/+source/gnome-vfs2/+bug/58672) and especially here [http://bugzilla.gnome.org/show_bug.cgi?id=363400](http://bugzilla.gnome.org/show_bug.cgi?id=363400) and write your comments/experiences to solve this annoying problem asap.

---

