---
title: "Creating a new partition"
date: 2009-02-13
forum: General Help
---

### Post by dox_drum on 2009-02-13
Hi there!

As far as I know, it is possible to make a new partition using Gparted, and using the LiveCD. However, I don't have the CD, and in any attempt to get it, I finish with an useless CD (or DVD), 'cause it said to have errors.

Is there a way to do a partition without the LiveCD?

The result of **df -h** is

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3             137G   50G   80G  39% /
tmpfs                1008M     0 1008M   0% /lib/init/rw
varrun               1008M  348K 1008M   1% /var/run
varlock              1008M     0 1008M   0% /var/lock
udev                 1008M  2.9M 1005M   1% /dev
tmpfs                1008M  776K 1007M   1% /dev/shm
lrm                  1008M  2.0M 1006M   1% /lib/modules/2.6.27-11-generic/volatile

```
And I'd like to have a swap partition of about 2GB.

Thank you all.

By the way... What are all those little partition for? ... Yeah, I have no idea because I bought this computer pre-installed, and I've been lazy of backing up my files to re-install Ubuntu.

[CENTER]Enjoy![/CENTER]

---

### Post by kanikilu on 2009-02-13
You can use GParted at any time, the only catch is that you cannot modify a drive that has mounted partitions. So, if you are trying to partition the drive that already has Ubuntu installed, I don't believe you can do that without a live CD.

There are other live CD options, though. Knoppix includes GParted, and GParted even has a standalone live CD/USB: [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by kestrel1 on 2009-02-13
If you want to be able to re-partition your HD you will need the Live CD, as it looks like this is your main drive, right?
You cannot re-partition if the drive is mounted.
Using df -h isn't really showing you what you want try this instead```
sudo fdisk /dev/sda -l
```
Post the result.

---

### Post by dox_drum on 2009-02-13
> **kestrel1 said:**
> If you want to be able to re-partition your HD you will need the Live CD, as it looks like this is your main drive, right?
You cannot re-partition if the drive is mounted.
Using df -h isn't really showing you what you want try this instead```
sudo fdisk /dev/sda -l
```
Post the result.

Here is the result!

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x60000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          11       88326   de  Dell Utility
/dev/sda2              12         664     5245222+   b  W95 FAT32
/dev/sda3   *         665       18703   144898267+  83  Linux
/dev/sda4           18704       19457     6056505    5  Extended
/dev/sda5           18704       19457     6056473+  82  Linux swap / Solaris

```

So, in fact I have a swap partition, Isn't it?

Thanks!

---

### Post by kestrel1 on 2009-02-13
Yes, you have a swap :)
If you want to repartition this though, you will need the live CD as said previously or use the live gparted CD (see link from kanikilu)

---

### Post by bodhi.zazen on 2009-02-13
Actually, can you post the output of

```
free -m
```

---

### Post by dox_drum on 2009-02-15
> **bodhi.zazen said:**
> Actually, can you post the output of

```
free -m
```

Here it is!

```
oscar@dell-desktop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          2014       1871        143          0         68       1181
-/+ buffers/cache:        621       1393
Swap:         5914          1       5912
```

---

### Post by bodhi.zazen on 2009-02-15
That command shows an active (and large) swap partition :

 [COLOR=green]Swap:         5914          1       5912[/COLOR]

---

### Post by kestrel1 on 2009-02-16
I would suggest that the size of the swap if far too big.
I would be inclined to at least half that size if not less. How much RAM do you have onboard?

---

### Post by dox_drum on 2009-02-16
> **kestrel1 said:**
> I would suggest that the size of the swap if far too big.
I would be inclined to at least half that size if not less. How much RAM do you have onboard?

I've just 2GB of RAM, and the architecture supports up to 3GB.

Why is it recommendable to resize down this swap partition?

---

### Post by phantom3113 on 2009-02-16
SWAP (unless I'm mistaken) is used as a sort of RAM "overflow" if the available RAM isn't necessarily enough at the time. The recommended size for the SWAP partition is about 2 times the size of your RAM, max. Sizing this down leaves more space for whatever else. :)

---

### Post by geirha on 2009-02-16
> **dox_drum said:**
> I've just 2GB of RAM, and the architecture supports up to 3GB.

Why is it recommendable to resize down this swap partition?

Nah, just leave it be. The swap partition needs to be at least the size of physical RAM in order to be able to hibernate, so you can get 3-4 GB more for your linux partition if you shrink it, but in my opinion it's not worth the fuzz.

---

### Post by kestrel1 on 2009-02-16
I would be inclined to agree to leave the swap as it is at present, as I have seen more problems caused by resizing than it is worth.
I would resize it if you need to re-install at any stage. It shouldn't cause any problems, I just don't see the point in having a chunk of HD space taken up by swap.

---

### Post by dox_drum on 2009-02-16
Thank you all guys!

---

### Post by bodhi.zazen on 2009-02-16
You can create new partitions with gparted.

gparted is on the live CD but not installed by default.

If you wish to use the command line, use fdisk and mkfs.ntfs

---

