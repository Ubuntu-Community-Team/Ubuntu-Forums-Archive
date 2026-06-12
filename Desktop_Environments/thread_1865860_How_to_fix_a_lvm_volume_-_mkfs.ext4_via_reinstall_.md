---
title: "How to fix a lvm volume - mkfs.ext4 via reinstall messed up the lvm ext4 fs"
date: 2011-10-20
forum: Desktop Environments
---

### Post by bababooey on 2011-10-20
My Lucid box has cryptsetup and once I enter my password, my lvm volumes maps to / /home and swap. During my reinstall, I normally just mark my /root lvm and /swap lvm and leave out /home's volume. I then add the lvm /home volume after the install is finished by using /etc/fstab so I have all my personal files in tact.

Well today I slipped up and marked the /home volume to be used as /home in the ubuntu install gui, and killed it possibly 20%-50% of the install running mkfs.ext on it. I can no longer mount the lvm home volume and dmesg shows after a manual mount /dev/mapper/vg1-home /home shows

[ 1116.624291] EXT4-fs (dm-3): VFS: Can't find ext4 filesystem

Do I have a chance to fix it? Even though my LVM volumes are not encrypted, Im guessing itheres a good chance I can recover files. But is there another way I can fix the ext4fs since is broken, but also somehow someway get my files back in the filesystem? 

If thats not a possibility, besides testdisk, what else can I use specifically for ext4? I noticed programs like recover, and a few others in synaptic, works only on ext2. I installed foremost but never used it before. 

Any help would be very much appreciated. Thanks

---

### Post by bababooey on 2011-10-20
Also if i run testdisk should I continue to fix the new ext4 fs, either using mkfs.ext or fsck? 
Or just leave the half created fs? And do a deeper search in testdisk?

Currently if I run testdisk, I see ntfs, fat12 references, but this drive has never had such filesystems but this is just 3% 

  ext3                           0 1025384447 1025384448
  ext3                           0 1025384447 1025384448
  ext3                           0 1025384447 1025384448
  ext3                           0 1025384447 1025384448
  ext3                           0 1025384447 1025384448
Warning: Incorrect number of heads/cylinder 16 (NTFS) != 1 (HD)
Warning: Incorrect number of sectors per track 2 (NTFS) != 1 (HD)
  NTFS                    18248599   18254772       6174
Warning: Incorrect number of heads/cylinder 16 (NTFS) != 1 (HD)
Warning: Incorrect number of sectors per track 2 (NTFS) != 1 (HD)
  NTFS                    18254772   18260945       6174 [Boot]
Warning: Incorrect number of heads/cylinder 4 (FAT) != 1 (HD)
Warning: Incorrect number of sectors per track 17 (FAT) != 1 (HD)
  FAT12                   18261060   18281798       20739 [NO NAME

---

