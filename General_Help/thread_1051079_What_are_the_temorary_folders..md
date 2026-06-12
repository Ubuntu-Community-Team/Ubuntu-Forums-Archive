---
title: "What are the temorary folders."
date: 2009-01-26
forum: General Help
---

### Post by Hillshum on 2009-01-26
Hello, Thanks for the great OS.

I am on xubuntu intrepid, but I think this is a more general question. I have a 3GB HDD and am running out of room. Where are the temp folders?

All help appreciated,
Hillshum

---

### Post by BrandonBan6 on 2009-01-26
temp files by default are stored in /tmp, but these files are wiped (or should be) at reboot. Do you have data that can be moved to an external or remote location?

---

### Post by Hillshum on 2009-01-26
Only application binaries really. I've been cleaning my Firefox cache regularly.

---

### Post by oldos2er on 2009-01-26
If you've got room to install one more program, install the package localepurge; it should save you some disk space.

---

### Post by -kg- on 2009-01-26
> **Hillshum said:**
> Hello, Thanks for the great OS.

I am on xubuntu intrepid, but I think this is a more general question. I have a 3GB HDD and am running out of room. Where are the temp folders?

All help appreciated,
Hillshum

A 3 GB hard drive?  WOOF!  That's small!  Binaries are stored on / (root).  I have separate / and /home partitions.  According to GPartEd, my / partition is 9.31 GB and I show that 4.05 GB of that is used.  What I have used is more than your entire hard drive.

Now while I do have a few binaries installed that you probably wouldn't have, I would say that your hard drive is still mightily small for a distro like Ubuntu, even Xubuntu.  It's no wonder you're running out of room.

I would consider either upgrading your hard drive to at least a *little* larger or going with one of the smaller Linux distros, like [Puppy]("http://www.puppylinux.com/") (which apparently runs on a 64 MB Ramdisk) or [Damn Small Linux]("http://www.damnsmalllinux.org/") (which purportedly runs from a 50 MB footprint).

Obviously, you can run Xubuntu from a small hard drive, but it looks like it takes constant monitoring and work to keep it usable.  If possible, it would be much better if you could upgrade to, say, *at least* an 8 GB hard drive.  That's small, but you would much better be able to run Xubuntu (or Ubuntu, for that matter) on it.

Of course, this is just my opinion, and you might have a reason you're running that way, but it seems like such a PITA to keep that type of configuration going.

---

### Post by der_joachim on 2009-01-27
Have you cleaned the apt cache? Apt stores every file it downloads and if you do nothing about it, it will indefinitely do so. Luckily, you can easily clean your cache by using the following command:
```

sudo aptitude clean

```
or 
```

sudo aptitude autoclean

```

The difference between the two commands is that *autoclean* only clears the obsolete packages from the cache, while *clean* entirely empties it.

---

