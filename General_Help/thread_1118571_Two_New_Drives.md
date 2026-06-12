---
title: "Two New Drives"
date: 2009-04-07
forum: General Help
---

### Post by Rodney9 on 2009-04-07
I have two new sata 320Gig drives plus Ubuntu on a 160G and a old 80G with xp.

What would be the best way to use these two new 320's for backups between Ubuntu (mostly, 99% Ubuntu) and xp.
I thought to synchronize the two, but what format would be best, fat32 is old and can't use over 4G files, xp can't see ext3, is ntfs trustworthy, at least Ubuntu can read/write it.

Rodney.

---

### Post by kpkeerthi on 2009-04-07
Go with ext3. Windows could use [this]("http://www.fs-driver.org/") to see it.

---

### Post by Rodney9 on 2009-04-08
> **kpkeerthi said:**
> Go with ext3. Windows could use [this]("http://www.fs-driver.org/") to see it.

The "Ext2 Installable File System for Windows" software wont support Inodes that are larger than 128 bytes .
Ubuntu 8.10 uses 256 bytes.
However I found Ext2Fsd – [http://sourceforge.net/projects/ext2fsd/](http://sourceforge.net/projects/ext2fsd/)
which does.

---

### Post by coffeecat on 2009-04-08
> **Rodney9 said:**
> is ntfs trustworthy, at least Ubuntu can read/write it.

I've found read/write with NTFS very reliable since Hardy. NTFS is prone to fragmentation but, so long as you keep running Windows, you've got Windows for defragging and repair of the filesystem with chkdsk should it be damaged. Also, I find the *lack* of support for Linux permissions in NTFS to be a positive advantage in this single-user household.

Be warned that there's a very minor bug in Jaunty - I don't know whether it's the same in Intrepid. If you use the Jaunty installer to set up an fstab entry, you get:

```
device    mountpoint    ntfs        defaults,nls=utf8,umask=007,gid=46    0 1
```Which is fine, but if you do a GUI copy from an ext3 partition to a NTFS partition mounted with this line, the date and time stamps are changed. (This doesn't happen with automounted NTFS devices.) Of course, you won't be using the installer, so instead use this line in fstab:

```
device    mountpoint    ntfs        defaults    0 0
```and you don't get the date/time problem. That's the fstab line I use.

---

### Post by phreaknite on 2009-04-08
Well, I have been having a bit of a problem with ext2FSD with Ubuntu 8.10.

The problem is that Vista can only run it with signed driver checking turned off or in Test Mode.  The first is risky on Vista and the second is not really as seamless as I would like since each attempt to r/w from the drive would have to be premeditated and rebooted into TestMode Vista.

Can Ubuntu 8.10 be used on a drive with 128 inode?  If that is the case I may use ext2IFS...

If so, what is the drawback of using 128 vs. 256?

Else, is there a good work around for getting Ext2FSD to work with non-Test Mode vista?

---

