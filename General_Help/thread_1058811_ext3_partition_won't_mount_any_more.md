---
title: "ext3 partition won't mount any more"
date: 2009-02-03
forum: General Help
---

### Post by madsporkmurderer on 2009-02-03
My media/fileserver won't boot. I've got it up with a live disk and diagnosed that there is something wrong with the main OS partition (data is stored on separate drives).

I've tried "sudo mount -t ext3 /dev/sdb1 tmp" and got the standard:
```
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

dmesg|tail gives:
```
ubuntu@ubuntu:~$ dmesg | tail
[ 1248.966869] sd 1:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[ 1248.966998] sd 1:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 1248.967116] sd 1:0:0:0: [sda] 488397168 512-byte hardware sectors (250059 MB)
[ 1248.967171] sd 1:0:0:0: [sda] Write Protect is off
[ 1248.967178] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[ 1248.967277] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 1248.967376] sd 1:0:1:0: [sdb] 60058656 512-byte hardware sectors (30750 MB)
[ 1248.967430] sd 1:0:1:0: [sdb] Write Protect is off
[ 1248.967437] sd 1:0:1:0: [sdb] Mode Sense: 00 3a 00 00
[ 1248.967538] sd 1:0:1:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA

```

Is there a way this can be recovered so that I don't have to start over with configuration/programs etc?

Thanks in advance,
Mike

---

### Post by drs305 on 2009-02-03
Try:
```
sudo mount -t ext3 /dev/sdb1 **/tmp**
```
"tmp" probably doesn't exist, but "/tmp" does.

---

### Post by madsporkmurderer on 2009-02-03
Sorry I forgot to say, I created tmp

---

### Post by Neural oD on 2009-02-03
see drs305 post about tmp vs /tmp

---

### Post by madsporkmurderer on 2009-02-03
I know that /tmp will always exist as it is a system created directory. I used mkdir tmp to create /home/ubuntu/tmp, this is where I am trying to mount the partition

---

### Post by albinootje on 2009-02-03
> **madsporkmurderer said:**
>  I've got it up with a live disk and diagnosed that there is something wrong with the main OS partition (data is stored on separate drives).

I've tried "sudo mount -t ext3 /dev/sdb1 tmp" and got the standard:
<code>mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so</code>


Can you, still from the live cd, post the output of :
```

sudo fdisk -l
sudo fsck /dev/sdb1

```

---

### Post by Neural oD on 2009-02-03
ok - just make sure the permissions are correct - and make sure that you are sending it to the /home/ubuntu/tmp folder - and not a file

---

### Post by madsporkmurderer on 2009-02-03
```

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00024779

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       30401   244196001   83  Linux

Disk /dev/sdb: 30.7 GB, 30750031872 bytes
255 heads, 63 sectors/track, 3738 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9a959a95

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        3645    29278431   83  Linux
/dev/sdb2            3646        3738      747022+   5  Extended
/dev/sdb5            3646        3738      746991   82  Linux swap / Solaris

Disk /dev/sdc: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9eb4d58e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       24321   195358401   83  Linux

```

```

ubuntu@ubuntu:~$ sudo fsck /dev/sda1
fsck 1.41.3 (12-Oct-2008)
e2fsck 1.41.3 (12-Oct-2008)
/dev/sda1 has gone 334 days without being checked, check forced.
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
/dev/sda1: 156032/30539776 files (2.1% non-contiguous), 48990612/61049000 blocks

```

---

### Post by albinootje on 2009-02-03
> **madsporkmurderer said:**
> 
ubuntu@ubuntu:~$ sudo fsck /dev/sda1

Thanks.
In your OP you mention /dev/sdb1 as the file system giving problems to mount.
Is /dev/sda having your Linux installation ? Can you run the file system check on the other ext3 partitions too ?

---

### Post by madsporkmurderer on 2009-02-03
Silly me, sdb1 is the one that won't work- just running fsck on it

---

### Post by madsporkmurderer on 2009-02-03
Here we go, it's found the problem (not sure how to fix it though)

```
ubuntu@ubuntu:~$ sudo fsck /dev/sdb1
fsck 1.41.3 (12-Oct-2008)
e2fsck 1.41.3 (12-Oct-2008)
/dev/sdb1: Attempt to read block from filesystem resulted in short read while reading block 1544

/dev/sdb1: Attempt to read block from filesystem resulted in short read reading journal superblock

fsck.ext3: Attempt to read block from filesystem resulted in short read while checking ext3 journal for /dev/sdb1

```

---

### Post by Neural oD on 2009-02-04
not sure if this will help but look at testdisk. This should help you recover a bad partition setup - or even be able to get the data out! It's in one of the repos - but check out their website too - for documentation etc

---

