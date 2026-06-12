---
title: "lost /home drive"
date: 2010-05-29
forum: Dell Ubuntu Support (CLOSED)
---

### Post by pneaveill on 2010-05-29
Disclaimer:  Searched for almost 45 mins on the forums here without finding a similar post, so assuming this one is new. Apologies if somehow missed a previous post.

Did fresh install of ubuntu 10.4 on Dell Dimension.  Lost the former /home directory on /dev/sdb1.  

Steps to rectify:
(1) assumed that something gummed up at the install, so redid (2x)
(2) followed the steps [https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving) and [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome) and refuses to reboot into the old /home drive/directory

blkid =
```
/dev/sda1: UUID="939b39df-41cb-49ff-a388-7a0b4c02cc00" TYPE="ext4" 
/dev/sda5: UUID="5edd976b-c722-484b-abe2-b4875a960d46" TYPE="swap" 
/dev/sdb1: UUID="945a9efc-a44c-412c-8399-63f45f48823f" TYPE="ext3"]
```/etc/fstab```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=5edd976b-c722-484b-abe2-b4875a960d46 none            swap    sw              0       0
UUID=945a9efc-a44c-412c-8399-63f45f48823f /home ext3 nodev,nosuid  0 2

/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```

---

### Post by oldfred on 2010-05-29
Is it just not booting or is it giving a specific message on the /home or its UUID as not able to mount??

---

### Post by pneaveill on 2010-05-29
> **oldfred said:**
> Is it just not booting or is it giving a specific message on the /home or its UUID as not able to mount??

 Can boot on the computer, just gives error about the drive

---

### Post by oldfred on 2010-05-29
Try this and see if you get a better error message.

From the terminal - This reloads fstab
sudo mount -a

---

### Post by pneaveill on 2010-05-29
> **oldfred said:**
> Try this and see if you get a better error message.

From the terminal - This reloads fstab
sudo mount -a
Appreciate the promptness with responses.

Totally forgot which log file would show that error, but said it was serious error.  REbooted and "lost" the good /home

---

### Post by teward on 2010-05-29
only thing I can think of is that your install accidentially overwrote the "good" /home drive with a clean partition... *shrugs*

---

### Post by pneaveill on 2010-05-29
only looked like it erased it. CHanged the fstab and reran the sudo mount -a and it shows up and can access it, but as /media/home not /home

apologies if mislead or misspoke at all

---

### Post by oldfred on 2010-05-30
If your fstab still is as posted and your run the mount -a without any errors it has to be mounting it correctly. The /media/home looks like just a default mount not a fstab mount.

---

### Post by gbrainin on 2010-05-31
Comparing this to my /etc/fstab, I notice a couple of differences.  First, there is no comment line before the line for the /home directory.  Something like:
```
# /home was on /dev/sdb1 during installation
```
Which makes me wonder if it didn't get recognized properly during the installation process.  Second, on mine instead of specific switches, I just have the word "defaults."
As an experiment, why not try changing the line to something like this:
```
/dev/sdb1 /home ext3 defaults  0 2
```
If that works, then you can start working backwards to get it to work with a UUID and specific switches.  If not, then I'm wondering if it's a hardware problem (since your /home is on a separate physical drive).

---

### Post by pneaveill on 2010-05-31
> **gbrainin said:**
> Comparing this to my /etc/fstab, I notice a couple of differences.  First, there is no comment line before the line for the /home directory.  Something like:
```
# /home was on /dev/sdb1 during installation
```Which makes me wonder if it didn't get recognized properly during the installation process.  Second, on mine instead of specific switches, I just have the word "defaults."
As an experiment, why not try changing the line to something like this:
```
/dev/sdb1 /home ext3 defaults  0 2
```If that works, then you can start working backwards to get it to work with a UUID and specific switches.  If not, then I'm wondering if it's a hardware problem (since your /home is on a separate physical drive).

Sorry, needed a break from the computer yesterday.  Attempted your suggestion and here is the new fstab and results
```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=5edd976b-c722-484b-abe2-b4875a960d46 none            swap    sw              0       0

/dev/sdb1 /home ext3 defaults 0 2

# user edit:
# UUID=945a9efc-a44c-412c-8399-63f45f48823f /media/home ext3 nodev,nosuid  0 2
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```

FOr the record (though am not sure totally what am looking at)```

fsck from util-linux-ng 2.17.2 
fsck from util-linux-ng 2.17.2 
/dev/sda1: clean, 192093/4702208 files, 1529121/18794240 blocks 
/dev/sdb1: The filesystem size (according to the superblock) is 9769520 blocks 
The physical size of the device is 9767512 blocks 
Either the superblock or the partition table is likely to be corrupt! 
 
 
/dev/sdb1: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY. 
    (i.e., without -a or -p options) 
mountall: fsck /home [271] terminated with status 4 
mountall: Filesystem has errors: /home 
Attempting to fix /home filesystem 
fsck from util-linux-ng 2.17.2 
e2fsck 1.41.11 (14-Mar-2010) 
The filesystem size (according to the superblock) is 9769520 blocks 
The physical size of the device is 9767512 blocks 
Either the superblock or the partition table is likely to be corrupt! 
Abort? yes 
 
mountall: fsck /home [601] terminated with status 8 
mountall: Unrecoverable fsck error: /home 
Skipping /home at user request 
 * Starting AppArmor profiles       [80G Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox 
 [74G[ OK ] 
 * Setting sensors limits       [80G  [74G[ OK ]
```

---

### Post by jarviser on 2010-05-31
Can I assume that this is a USB drive? Has anyone else, I wonder, successfully installed Ubuntu with /home on an external drive? I have seen other reports of fsck errors with external drives on /home. 
 /media/home seems to be the right place for a usb drive.

If it's not a USB drive, ignore this rambling...

---

### Post by pneaveill on 2010-05-31
> **jarviser said:**
> Can I assume that this is a USB drive? Has anyone else, I wonder, successfully installed Ubuntu with /home on an external drive? I have seen other reports of fsck errors with external drives on /home. 
 /media/home seems to be the right place for a usb drive.

If it's not a USB drive, ignore this rambling...


It is, in fact, an internal ATA drive not external

---

### Post by gbrainin on 2010-05-31
Have you tried doing what it suggests, and running fsck manually?```
fsck /dev/hdb1
```

---

### Post by oldfred on 2010-05-31
This may be better:

Must be unmounted:
Try "e2fsck -f /dev/sdb1". Ordinarily, fsck skips most of the check if the filesystem is marked as clean. The "-f" option to e2fsck (note: e2fsck, not fsck) forces a full check even if the filesystem is marked as clean.

From liveCD so everything is unmounted
sudo e2fsck -C0 -p -f -v /dev/sdb1
if errors:
sudo e2fsck -f -y -v /dev/sdb1

---

### Post by pneaveill on 2010-05-31
> **oldfred said:**
> This may be better:

Must be unmounted:
Try "e2fsck -f /dev/sdb1". Ordinarily, fsck skips most of the check if the filesystem is marked as clean. The "-f" option to e2fsck (note: e2fsck, not fsck) forces a full check even if the filesystem is marked as clean.  

```
paul-desktop:~# e2fsck -f /dev/sdb1
e2fsck 1.41.11 (14-Mar-2010)
The filesystem size (according to the superblock) is 9769520 blocks
The physical size of the device is 9767512 blocks
Either the superblock or the partition table is likely to be corrupt!
Abort<y>? no

Pass 1: Checking inodes, blocks, and sizes
Error reading block 9767752 (Invalid argument) while reading indirect blocks of inode 2428593.  Ignore error<y>? yes

Force rewrite<y>? yes

Error writing block 9767752 (Invalid argument) while reading indirect blocks of inode 2428593.  Ignore error<y>? yes

Inode 2428593, i_blocks is 2152, should be 104.  Fix<y>? yes

Error reading block 9768037 (Invalid argument) while reading indirect blocks of inode 2428609.  Ignore error<y>? yes

Force rewrite<y>? yes

Error writing block 9768024 (Invalid argument).  Ignore error<y>? yes

Couldn't fix parent of inode 2428608: Couldn't find parent directory entry

Pass 4: Checking reference counts
Pass 5: Checking group summary information

/dev/sdb1: ***** FILE SYSTEM WAS MODIFIED *****

/dev/sdb1: ********** WARNING: Filesystem still has errors **********

/dev/sdb1: 17110/2444624 files (13.5% non-contiguous), 1281202/9769520 blocks 
```
> 
From liveCD so everything is unmounted
sudo e2fsck -C0 -p -f -v /dev/sdb1
if errors:
sudo e2fsck -f -y -v /dev/sdb1

---

### Post by pneaveill on 2010-05-31
Guess at this point, should I wipe the drive and remount and all that, then transfer the stuff back over? If so, then how would I go about it?

---

### Post by pneaveill on 2010-06-01
> **oldfred said:**
> This may be better:

Must be unmounted:
Try "e2fsck -f /dev/sdb1". Ordinarily, fsck skips most of the check if the filesystem is marked as clean. The "-f" option to e2fsck (note: e2fsck, not fsck) forces a full check even if the filesystem is marked as clean.

From liveCD so everything is unmounted
sudo e2fsck -C0 -p -f -v /dev/sdb1
if errors:
sudo e2fsck -f -y -v /dev/sdb1

Result as you suggested:

```
root@ubuntu:~# sudo e2fsck -f -y -v /dev/sdb1
e2fsck 1.41.11 (14-Mar-2010)
The filesystem size (according to the superblock) is 9769520 blocks
The physical size of the device is 9767512 blocks
Either the superblock or the partition table is likely to be corrupt!
Abort? yes
```

---

### Post by pneaveill on 2010-06-12
Taken a while and apologize for the delay.  Been running some tests on the drive and have determined it is, indeed, bad and will be replaced as soon as income comes in.  Appreciate all the assistance in this endeavor thus far.


Note to moderators: am uncertain how to close. Please advise.

---

