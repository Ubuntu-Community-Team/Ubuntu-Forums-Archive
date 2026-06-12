---
title: "Cant format unformatted space on mounted drive"
date: 2011-11-29
forum: Desktop Environments
---

### Post by mister_p_1998 on 2011-11-29
Hi all,
I've got a 1.5 TB drive mounted as sdb1, 1 tb is formatted as ext3 and mounted. I finally got around to needing the last 500mb of space and tried to format it to ext3. I made a new extended partition, but it wont let me format it to any format (ext2, ext3 or whatever) Is it because the drive is already mounted? Do I have to unmount the whole drive to format the unused space? I tried making it a primary partition as well as extended, still no joy what am I doing wrong?
Steve

---

### Post by coffeecat on 2011-11-29
I'm a bit puzzled here:

> **mister_p_1998 said:**
> I made a new extended partition, but it wont let me format it to any format (ext2, ext3 or whatever)

You can have only one extended partition per drive and you don't format an extended partition because its sole purpose is to act as a container for logical partitions. There might be a mounting problem preventing you from creating new partitions, but let's look at your setup to see. Post the output of:

```
sudo fdisk -lu
mount
```

---

### Post by mister_p_1998 on 2011-11-29
> **coffeecat said:**
> I'm a bit puzzled here:



You can have only one extended partition per drive and you don't format an extended partition because its sole purpose is to act as a container for logical partitions. There might be a mounting problem preventing you from creating new partitions, but let's look at your setup to see. Post the output of:

```
sudo fdisk -lu
mount
```

I should have said I made AN extended partition... the first one is a primary...

---

### Post by mcduck on 2011-11-29
> **mister_p_1998 said:**
> I should have said I made AN extended partition... the first one is a primary...

You'll still need to create a logical partition inside the extended one, and then format the logical partition.

Like coffeecat said, extended partition is just a container for logical partitions, you can't use it for anything else.

---

### Post by mister_p_1998 on 2011-11-29
Ok heres  the output:

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x31853184

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   387744839   193872388+  83  Linux
/dev/sda2       387744840   390716864     1486012+   5  Extended
/dev/sda3       390716865   781417664   195350400   83  Linux
/dev/sda4       781417665  1953520064   586051200   83  Linux
/dev/sda5       387744903   390716864     1485981   82  Linux swap / Solaris

This is the drive in Question
################################################################################
Disk /dev/sdb: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00093e4e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63  2047998329  1023999133+  83  Linux

#################################################################################

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xcad7cad7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63   312560639   156280288+   7  HPFS/NTFS

Mount:

proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-29-generic/volatile type tmpfs (rw)
/dev/mapper/sda3 on /storage type ext3 (rw)
/dev/mapper/sda4 on /Storage2 type ext3 (rw)
/dev/mapper/sdb1 on /media/Samsung type ext3 (rw)
securityfs on /sys/kernel/security type securityfs (rw)
nfsd on /proc/fs/nfsd type nfsd (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/steve/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=steve)

---

### Post by mister_p_1998 on 2011-11-29
Gparted gives the following error:

GParted 0.3.5

Libparted 1.7.1

Format /dev/sdb5 as ext3  00:01    ( ERROR )
     	
calibrate /dev/sdb5  00:00    ( SUCCES )
     	
path: /dev/sdb5
start: 2047998393
end: 2930272064
size: 882273672 (420.70 GiB)
set partitiontype on /dev/sdb5  00:01    ( SUCCES )
     	
new partitiontype: ext3
create new ext3 filesystem  00:00    ( ERROR )
     	
mkfs.ext3 /dev/sdb5
     	
mke2fs 1.40.8 (13-Mar-2008)
/dev/sdb5 is apparently in use by the system; will not make a filesystem here!

========================================
Steve

---

### Post by mcduck on 2011-11-29
based on your above post you don't even *have* such partiton as /dev/sdb5, the /dev/sdb only has one partition (sdb1). On the other hand there is sda5, which is your swap and of course that would be in use...

Are you absolutely sure you are trying to format a partition on the correct drive?

---

### Post by mister_p_1998 on 2011-11-29
SDB5 is the extended partition created by gparted. I can create it, but cant format it.

---

### Post by mcduck on 2011-11-29
> **mister_p_1998 said:**
> SDB5 is the extended partition created by gparted. I can create it, but cant format it.

Like already said, you can't use extended partition for filesystems. Create a primary partition or a logical partition (inside the extended partition) instead.

---

### Post by mister_p_1998 on 2011-11-29
Thats what Im saying!
I DID create an extended partition, 
I DID create a logical partition!
 I cant format it though!

---

### Post by LinuxFan999 on 2011-11-29
Are you still using 8.04 and 8.10 as your signature says?

If so, keep in mind that the desktop version of 8.04 is end-of-life now, and both the desktop and server editions of 8.10 are also 
end-of-life.

I think you should have originally formatted the *_whole_* drive at the same time when you bought it, instead of formatting just 1TB at first, then the remaining 500GB later.

---

### Post by coffeecat on 2011-11-30
> **mister_p_1998 said:**
> SDB5 is the extended partition created by gparted. I can create it, but cant format it.

> **mister_p_1998 said:**
> Thats what Im saying!
I DID create an extended partition, 
I DID create a logical partition!
 I cant format it though!

From the information you've posted, I can see no evidence of an extended partition. sdb5 is a logical partition by definition - any partition numbered 5 and upwards is logical. The extended partition to contain that would be sdb2, sdb3 or sdb4, since you already have a primary partition sdb1.

The fdisk output you posted shows only the primary partition sdb1, so did you attempt to create the extended and logical partitions after you ran fdisk? I suggest you run "sudo fdisk -lu" again to see what fdisk makes of your partition table.

---

### Post by mister_p_1998 on 2011-11-30
> **coffeecat said:**
> From the information you've posted, I can see no evidence of an extended partition. sdb5 is a logical partition by definition - any partition numbered 5 and upwards is logical. The extended partition to contain that would be sdb2, sdb3 or sdb4, since you already have a primary partition sdb1.

The fdisk output you posted shows only the primary partition sdb1, so did you attempt to create the extended and logical partitions after you ran fdisk? I suggest you run "sudo fdisk -lu" again to see what fdisk makes of your partition table.

Yes, because when I failed to format the logical partition, I deleted it again.
Heres the output, now with the SDB1 extended partition:
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x31853184

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   387744839   193872388+  83  Linux
/dev/sda2       387744840   390716864     1486012+   5  Extended
/dev/sda3       390716865   781417664   195350400   83  Linux
/dev/sda4       781417665  1953520064   586051200   83  Linux
/dev/sda5       387744903   390716864     1485981   82  Linux swap / Solaris

Disk /dev/sdb: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders, total 2930277168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00093e4e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63  2047998329  1023999133+  83  Linux
/dev/sdb2      2047998330  2930272064   441136867+   5  Extended

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xcad7cad7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63   312560639   156280288+   7  HPFS/NTFS

---

### Post by coffeecat on 2011-11-30
One thing I noticed from your mount output is that three partitions are being mounted to /dev/mapper:

> **mister_p_1998 said:**
> /dev/mapper/sda3 on /storage type ext3 (rw)
/dev/mapper/sda4 on /Storage2 type ext3 (rw)
/dev/mapper/sdb1 on /media/Samsung type ext3 (rw)

/dev/mapper is used for RAID, LVM and encrypted partitions. If you're using encrypted partitions, then that will probably be irrelevant to your problem. If those drives were once used in RAID arrays and there is still residual RAID metadata on them, that *might* be a problem.

Whatever, I can see no reason why Gparted is failing to format a logical partition in your sdb2. (sdb2 is your extended partition, by the way. I guess your "now with the SDB1 extended partition" in your previous post is a typo). If you were using Gparted from your permanent installation, have you tried Gparted from the live CD?

One minor detail: the first root partition line is missing from your mount output - I guess a copy and paste omission - not that that makes any difference to the issue at hand.

---

### Post by mister_p_1998 on 2011-11-30
> **coffeecat said:**
> One thing I noticed from your mount output is that three partitions are being mounted to /dev/mapper:



/dev/mapper is used for RAID, LVM and encrypted partitions. If you're using encrypted partitions, then that will probably be irrelevant to your problem. If those drives were once used in RAID arrays and there is still residual RAID metadata on them, that *might* be a problem.



Whatever, I can see no reason why Gparted is failing to format a logical partition in your sdb2. (sdb2 is your extended partition, by the way. I guess your "now with the SDB1 extended partition" in your previous post is a typo). If you were using Gparted from your permanent installation, have you tried Gparted from the live CD?



No not RAID/LVM or Encrypted, I think I copied the /dev/mapper from my old setup on Dapper (!) 

Yeah, I was thinking of trying to format from a live CD rater than the booted drive, it said SDB2 was in use by the system when I tried to format? Why? it wasnt mounted? Im still running Hardy because its running sweetly and I dont want the hassle of backing up and restoring. When Server support expires, I'll probably upgrade, otherwise I'll carry on with my out of date stable system :-)

Steve

---

### Post by mister_p_1998 on 2011-11-30
Fixed it!
I had to do it from a Live CD.
Strangely, Im getting the mount name showing on the desktop, and I cant get rid of it, no big problem, but a bit annoying when I already have a shortcut to the working partition on the desktop too. Storage, Storage2,Storage3 and Storage-4 are shortcuts to the partitions, and the mount shortcuts are Storage4 and Samsung.
Steve

---

