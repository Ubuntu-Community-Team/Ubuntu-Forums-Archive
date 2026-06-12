---
title: "[SOLVED] Partition HDD using CLI"
date: 2009-01-04
forum: General Help
---

### Post by boof1988 on 2009-01-04
I want to partition the second HDD (on a home network server, running Ubuntu 8.04.1 server) using CLI (operating system is on the first HDD).  Have tried reading the man pages for parted, mkfs, mke2fs etc. and there is so much info that I can't figure out how to do it.

Main goals are:
Use CLI to perform the needed tasks (since the HDD is on a server).
Create the partition table for the HDD.
Create a single partition on the HDD.
Use ext3 file-system for the partition.

---

### Post by Firestone on 2009-01-04
Try cfdisk for partitioning. It doesnt support ext3 though, but just select the Linux fs(#83 iirc) as option and convert it to ext3 after that with mke2fs.

---

### Post by boof1988 on 2009-01-04
> **Firestone said:**
> Try cfdisk for partitioning. It doesnt support ext3 though, but just select the Linux fs(#83 iirc) as option and convert it to ext3 after that with mke2fs.

Thanks for the help.  I just used cfdisk and it seemed to work pretty well.  Now I'll try to change the file-system type to ext3.

I (earlier) tried to use parted but it asked me the size of the partition (when I wanted to whole drive as one partition) and I don't know how to figure out what numbers (MB) to use for the "parted" commands.

Thanks again for the help.  :)

---

### Post by boof1988 on 2009-01-04
In the process of trying things, I have created a whole partition /dev/sdb and another /dev/sdb1???

```
/dev/sdb: LABEL="gx110data" UUID="6c605fa0-6497-48f9-8915-87ef589b87b8" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb1: UUID="8da16d7c-fd9b-4360-bf40-4a5547a45715" TYPE="ext2"
```

Think I would like to start from scratch again.

Think I'll try to delete the current partitioning and start over.  If anyone has any more advice, please let me know.

Thanks Again...

---

### Post by Irony on 2009-01-04
just do;

```
sudo cfdisk
```

It will do everything including formatting as ext3.

Alternately use the live CD and install gparted (if it not on the live CD);

```
sudo apt-get install gparted
```

Note your 2 HDD will show up as sdb something (note with gparted do each operation one at the time or else it will freeze up).

---

### Post by Irony on 2009-01-04
Note if it is your 2nd HDD you may have to do;

```
sudo cfdisk /dev/sdb
```

To see the 2nd HDD instead of the first HDD.

---

### Post by boof1988 on 2009-01-04
```
/dev/sdb: LABEL="gx110data" UUID="6c605fa0-6497-48f9-8915-87ef589b87b8" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb1: UUID="8da16d7c-fd9b-4360-bf40-4a5547a45715" TYPE="ext2"
```

Here is what I've done:

Deleted /dev/sdb1 using cfdisk.

Used...

```
sudo parted -i /dev/sdb mklabel
```

to remove the name for /dev/sdb.

And then used cfdisk to make one partition on the whole drive.

Now I just need to figure out how to make a LABEL for the /dev/sdb1.

@Irony,
I'm using ssh over my home network so I didn't think I could use gparted.  Can I use gparted over ssh without a "Desktop" interface?

---

### Post by boof1988 on 2009-01-04
Duh... (to myself)

Use...

```
sudo e2label /dev/sdb1 gx110data
```

to LABEL partition /dev/sdb1.

I still need to figure out how to make the file-system ext3.  It is ext2 currently.

---

### Post by logos34 on 2009-01-04
> **boof1988 said:**
> 
I still need to figure out how to make the file-system ext3.  It is ext2 currently.

**sudo tune2fs -j /dev/sdb1**

---

### Post by boof1988 on 2009-01-04
> **logos34 said:**
> **sudo tune2fs -j /dev/sdb1**

Thanks... I didn't see this until I already did it over using...

```
sudo mke2fs -c -j -L gx110data -v /dev/sdb1
```

Thanks Again to All...

---

### Post by bodhi.zazen on 2009-01-04
I usually use fdisk to make partitions and then the command line to make a file system.

Fdisk : [http://tldp.org/HOWTO/Partition/fdisk_partitioning.html](http://tldp.org/HOWTO/Partition/fdisk_partitioning.html)

Then to make a file system you can 

```
mkfs.ext3 /dev/sdb1
```

Depending on how you are looking at the file system it may appear as ext2

---

### Post by boof1988 on 2009-01-04
> **bodhi.zazen said:**
> I usually use fdisk to make partitions and then the command line to make a file system.

Fdisk : [http://tldp.org/HOWTO/Partition/fdisk_partitioning.html](http://tldp.org/HOWTO/Partition/fdisk_partitioning.html)

Then to make a file system you can 

```
mkfs.ext3 /dev/sdb1
```

Depending on how you are looking at the file system it may appear as ext2

I think I'll partition again using fdisk...  This is mostly a learning exercise anyway.

Thanks...

---

