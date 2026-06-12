---
title: "Unable to mount partition"
date: 2009-03-05
forum: General Help
---

### Post by prapanjganeshan on 2009-03-05
Hi, 

I have installed Ubuntu intrepid. Except for adding some environment variables and installing few softwares, I haven't modified any files. Today I was not able to sudo: It said user not in sudoers list. I then booted in recovery mode and edited the sudoers file. Now I am able to sudo. But, after this I am unable to mount any of my other partitions. I had no problem mounting the drives before. This is the error dialogue:

DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

And this is my fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk /               ext3    loop,errors=remount-ro 0       1
/host/ubuntu/disks/boot /boot           none    bind            0       0
/host/ubuntu/disks/home.disk /home           ext3    loop            0       2
/host/ubuntu/disks/usr.disk /usr            ext3    loop            0       2
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
~                                                                            
~                         

Please help .

Thank you

---

### Post by prapanjganeshan on 2009-03-05
And I ran sudo fdisk -l, got the following as output

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa72ba72b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3824    30716248+   c  W95 FAT32 (LBA)
/dev/sda2            3825       19456   125564040    f  W95 Ext'd (LBA)
/dev/sda5            3825        7648    30716248+   b  W95 FAT32
/dev/sda6            7649       13385    46082421    7  HPFS/NTFS
/dev/sda7           13386       19456    48765276    7  HPFS/NTFS

I hope someone has a solution

---

