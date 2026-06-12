---
title: "Need Help Extending Root Filesystem Using Additional Hard Drives on IBM Cloud Server"
date: 2024-09-10
forum: Debian
---

### Post by shahbazahmad444 on 2024-09-10
Hello everyone,
I’m working on an IBM cloud server running Debian and need some assistance with extending my root filesystem. Here are the details:
[B]Current Disk Layout:

[/B]
[B]lsblk output:

[/B]
*root@hanyg6266:~# lsblk*
*NAME    MAJ:MIN RM  SIZE RO TYPE MOUNTPOINTS*
*xvda    202:0    0  100G  0 disk *
*&#9500;&#9472;xvda1 202:1    0    1G  0 part /boot*
*&#9492;&#9472;xvda2 202:2    0   99G  0 part /*
*xvdb    202:16   0    2G  0 disk *
*&#9492;&#9472;xvdb1 202:17   0    2G  0 part [SWAP]*
*xvdc    202:32   0  400G  0 disk *
*xvde    202:64   0  400G  0 disk *
*xvdh    202:112  0   64M  0 disk *

**blkid output:**



*/dev/xvda2: LABEL="cloudimg-rootfs" UUID="25a4ce50-0329-4893-af97-c022d6f06853" BLOCK_SIZE="4096" TYPE="ext4" PARTUUID="37c5d9ea-02"*
*/dev/xvda1: LABEL="cloudimg-bootfs" UUID="98f1daa5-239d-4567-9976-cea79565dd15" BLOCK_SIZE="4096" TYPE="ext3" PARTUUID="37c5d9ea-01"*
*/dev/xvdh: SEC_TYPE="msdos" LABEL_FATBOOT="config-2" LABEL="config-2" UUID="9796-932E" BLOCK_SIZE="512" TYPE="vfat"*
*/dev/xvdb1: LABEL="SWAP-xvdb1" UUID="d51fcca0-6b10-4934-a572-f3898dfd8840" TYPE="swap" PARTUUID="00025cdb-01"*
[B]
df -hT output:

[/B]
*Filesystem     Type   Size  Used Avail Use% Mounted on*
*tmpfs          tmpfs  6.3G  1.2M  6.3G   1% /run*
*/dev/xvda2     ext4    98G  1.6G   92G   2% /*
*tmpfs          tmpfs   32G     0   32G   0% /dev/shm*
*tmpfs          tmpfs  5.0M     0  5.0M   0% /run/lock*
*/dev/xvda1     ext3   975M   74M  850M   8% /boot*
*tmpfs          tmpfs  6.3G   12K  6.3G   1% /run/user/0*





**Problem:**I want to extend my root filesystem to use the additional 400GB + 400GB hard drives (/dev/xvdc and /dev/xvde). However, I can't boot from a CD or ISO due to the lack of physical access. My SSH access is restricted to the current root directory, and I need to keep it operational while extending the root filesystem.
I’ve already mounted the partitions from the additional hard drives to /home, but they are not being used to extend the root filesystem. I can’t copy or move the root directory or resync it due to SSH access limitations.


**Request:**Can anyone guide me through the process of extending my root filesystem with these additional drives while keeping the system operational via SSH? Any step-by-step instructions or commands would be greatly appreciated!
Thank you in advance!

---

### Post by coffeecat on 2024-09-10
Not an Ubuntu question. *Thread moved to the **Debian** sub-forum.*

---

### Post by TheFu on 2024-09-10
Can you please edit your original post and wrap all the terminal output in forum code tags so the columns are maintained?

As it is now, I don't see a way to extend the file system. You didn't install with LVM which would have made something like this pretty easy.  Without LVM, you can't modify the size of a file system that is mounted.

However, you can use symbolic links to make specific directories redirect to different storage.  

I really need to see the output more clearly, with the correct columns to be certain.  I'd prefer to see these exact commands:
```
lsblk -e 7 -o name,type,fstype,size,FSAVAIL,FSUSE%,label,mountpoint
df -hT -x squashfs -x tmpfs -x devtmpfs
sudo fdisk -l
```
so the extra junk isn't there. We only want real storage, not fake storage.  The fdisk output, if you can, please don't post any loop devices that might be shown. They are useless.  Just the /dev/xvd* devices, please.

BTW, you will probably need to reboot the system.  It would all be easier if you could connect an ISO to the VM and boot off it, then do a fresh install with LVM into one of the larger, empty, disks, and migrate everything over to it.  Physical access shouldn't be necessary for any of this, but I've never used IBM x86 clouds, only AIX LPAR clouds on Power-based systems. It has been nearly 20 yrs since I had IBM training on that stuff, however. The entire world has changed and I don't remember any of it being odd or different from other hypervisor ideas I'd used over the decades.

---

