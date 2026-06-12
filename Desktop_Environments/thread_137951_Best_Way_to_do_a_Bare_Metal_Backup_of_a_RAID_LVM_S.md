---
title: "Best Way to do a Bare Metal Backup of a RAID LVM System"
date: 2006-03-01
forum: Desktop Environments
---

### Post by ThreeE on 2006-03-01
Hi all.  I have a Ubuntu Breezy Badger box (that I love dearly) with two 300GB SATA drives (/dev/sda and /dev/sdb) arranged in a RAID-1 array.  In addition, the entire filesystem, except /boot, is setup with LVM.

I'm always experimenting with new stuff on this box, so in the past (**before I used RAID and LVM and only had a single IDE drive (/dev/hda)**) I performed backups that allowed me to restore the system from bare metal.  I did it this way:

1) Boot the system using a Live CD (I typically use Knoppix).

2) Mount another networked filesystem:
```

su
mkdir /mnt/tombstone
mount -t smbfs -o username=[username] //192.168.#.###/homes /mnt/tombstone

```

3) Mount the drive to be backed up, zero out the blank space on the drive, and unmount the drive.
```

mkdir /mnt/hda1
mount /dev/hda1 /mnt/hda1
dd if=/dev/zero of=/mnt/hda1/bigzerofile
rm /mnt/hda1/bigzerofile
umount /mnt/hda1

```

4) Create a backup image
```

md5sum /dev/hda > /mnt/tombstone/image/md5.orig
dd if=/dev/hda | gzip > /mnt/tombstone/image/img.gz

```

This worked great.  To restore the drive, all I had to do was to repeat steps 1 and 2 and write the image back to the drive with:
```

gzip -dc /mnt/tombtone/image/img.gz | dd of=/dev/hda

```

Everything was peachy-keen.  The dd command caught everything -- including the Master Boot Record.  I found that the zeroing process in step 3 was crucial though -- without it, the backup image becomes as big as the drive.  With it, the image is quite small and manageable.

**So here's the kicker: with my new RAID/LVM setup, I can't perform step 3 -- the Live CD doesn't know anything about the underlying Volume Group and therefore effectively can't access the filesystem.**  RAID isn't a problem -- I can either just write the image to both disks or just one and do a RAID recovery.

The only thing I can think of is to write zero files to each of the Logical Volumes (LVs) in the Volume Group (VG) that fill the LVs up to 95% of their capacity and to create a blank LV to zero out the unused portion of the VG -- then proceed as before.

Is there a better way to do a bare metal recovery of a RAID/LVM setup?  I have also tried using LVM snapshots, but since I have multiple LVs in the VG, I'm concerned that I might get an inconsistent backup.  Each snapshot would be consistent, but since they would all be done at different times, the entire system would not be consistent.

I'm running 2.6.12-10-386 #1 Mon Jan 16 17:18:08 UTC 2006 i686 GNU/Linux on an AMD64 X2 4400+.

Thanks in advance.

---

### Post by joshuapurcell on 2006-03-01
LVMs try to make it so that you don't have to worry about the physical hard drive your partitions are located on, yet your choice of backup solution (using the **dd** command) is on the physical level, so I don't think they go well with each other. I have some notes (posted below) that shows what I did in order to restore backups of systems that had logical volumes.
Here's a brief overview of the setup I was working with: I had backups of all the partitions on a machine through the old **dump** command, and those partitions were mounted on an LVM. That system began having hardware problems and the backups needed to be restored on another identical machine. Here's the commands I used to take backups of the **/** and **/root** partitions (which were located in a script that was called while in single-user mode):```
dump -0 -j -A /backup/toc1_$today -f /backup/root_$today.dump -L "/_$today" / | tee -a /backup/$today.log
dump -0 -j -A /backup/toc2_$today -f /backup/boot_$today.dump -L "/boot_$today" /boot | tee -a /backup/$today.log
```These two lines actually backed up to the same disk (which was not very fault-tolerant), but I had multiple dump lines that I ran depending on if I was backing up to local/remote disk or local/remote tape. I was able to backup to the same disk using the **dump** command by using the **chattr -R +d /backup** command. You could just change the location to the mounted partition you mentioned if that works (and avoid using **chattr**).

The above creates backups of the logical partitions but not the physical layout on the hard drives (including LVM info). These commands will all give you this info:```
sudo sfdisk -d
sudo fdisk -l
sudo pvdisplay
sudo vgdisplay
sudo lvdisplay
```Once you are ready to restore the backups you've taken, you use the information from the above commands to recreate the LVM. Here's the steps I took (picking up at the part where you have booted up from some installCD or liveCD):```
Manually recreating the filesystem:
-use fdisk to recreate the needed partition tables on the available hard drives (hex code 8e for Linux LVM)
*in the following example, /dev/sda4 and /dev/sdb2 are the two LVM partitions created using fdisk
lvm pvcreate /dev/sda4 /dev/sdb2			#create the two physical volumes
lvm pvdisplay						#should show the two new physical volumes without a VG Name
lvm vgcreate Volume00 /dev/sda4 /dev/sdb2		#create the volume group and add the PVs
lvm vgdisplay						#should show the PVs added to the VG Volume00
*take the Total PE number from the printout, in this example that is 7675
lvm lvcreate -l 7675 Volume00 -n LogVol00		#creates the LV called LogVol00 using all of Volume00's PEs
lvm lvdisplay						#should show info for /dev/Volume00/LogVol00
mke2fs /dev/Volume00/LogVol00				#create the ext3 filesystem on the LV
mkdir /mnt/lv						#create the mount point
mount /dev/Volume00/LogVol00 /mnt/lv			#mounts the filesystem at /mnt/lv
df							#display filesystem information
mount							#check to make sure the LV is read/write and is ext2
```

---

### Post by fille on 2006-03-01
Hi,

have a look at the mondorescue project. Have a look at [http://www.mondorescue.org]("http://www.mondorescue.org") and [http://mondorescue.berlios.de]("http://mondorescue.berlios.de/")
You just can install it from the repositories.
```
sudo apt-get update
sudo apt-get install mondo
```

You can create bootable images from a live running system
```
mondoarchive
```

Regards,
F.

---

