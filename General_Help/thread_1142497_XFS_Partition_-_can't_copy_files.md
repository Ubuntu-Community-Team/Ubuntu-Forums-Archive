---
title: "XFS Partition - can't copy files"
date: 2009-04-29
forum: General Help
---

### Post by b3d3r on 2009-04-29
I know that this is probably a stupid question but I can't copy files on my newly created XFS partition. I have used Gparted to create XFS partition and once I'm entering it I can't copy files on it, nor can I create any folders.

What am i doing wrong?

Thanks in advance,
b3d3r

---

### Post by b3d3r on 2009-04-29
I have done it ;] I typed in terminal:

```
sudo chown -R b3d3r:b3d3r /media/disk
```

Although, I don't know if this is a proper way of doing this - I'm afraid one day Ubuntu will delete all the files from the disk ;]. Is this a proper way?

---

### Post by jowilkin on 2009-04-29
That should work fine.  What probably happened was you created the folder as root and so it was owned by root making it unwritable by non-root users.

A better way may be to mount it somewhere in your home directory where everything is owned by you (unless you want other users to be able to write to it).

---

### Post by b3d3r on 2009-04-29
Actually I have four partitions:

10 gigs XFS as /
2 gigs as SWAP
30 gigs XFS as /home
and rest ~200 gigs XFS as /media/disk

I have another question. If I reinstall Ubuntu, will I be still able to use /media/disk?

---

### Post by jowilkin on 2009-04-29
If you reinstall, use the manual partitioning method.  It will allow you to specify which partitions should be formatted and which should remain unchanged.

So yes it is fairly easy to reinstall and keep your partition.

---

