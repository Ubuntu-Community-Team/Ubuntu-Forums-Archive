---
title: "Rename volume lable of internal drive?"
date: 2009-01-20
forum: General Help
---

### Post by bg1256 on 2009-01-20
Well, after finally creating two new partitions and successfully applying permissions, and having them mount at boot (a learning experience for me!), I now need some help in renaming the volume labels for these partitions.

They are listed in fstab as follows:

/dev/sda2    /media/Multimedia
/dev/sdb3    /media/Documents


Currently, these volumes show up on my desktop, but the name that is displayed underneath the icons are:

238.1 GB Media 
68.0 GB Media

I would like to change those to "Multimedia" and "Documents" respectively.

I tried the guide here using e2label, but that has not worked: [https://help.ubuntu.com/community/RenameUSBDrive#ext2%20and%20ext3](https://help.ubuntu.com/community/RenameUSBDrive#ext2%20and%20ext3)

Any other tips?

---

### Post by Dieseler on 2009-01-21
Hey Bg

I used the gparted live disk to label my drives. I had the same problem and tried everything in the book to no avail. Theres a thread on how to do it here, How to fstab I believe it is named but in my opinion its less of a head ache to download the gparted disk, md5sum to ensure it is good then burn it and boot it up.
From there you can pick the disk and right click on the partitions and add labels.
Be careful not to do anything else to your partitions except label them though cause once its done,
It is done.

---

