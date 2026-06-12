---
title: "Creating a system image"
date: 2005-06-29
forum: Desktop Environments
---

### Post by edacsac on 2005-06-29
Heres a good one.

Now That I am just about configured the way I'd like to be, I want to create a bootable image CD for re-install/recovery/installing on another identical machine. In a windows enviroment, I know can do this across the the network using something like ghost. How can I do this in Ubuntu?

Could I get some input on accomplishing this? I bet samba is going to be one of the sticking points. If you wonder "why not just try creating a cd locally", well my cd burners are in my laptops, so I need to do this over the network.

Thanks!!!

---

### Post by alastair on 2005-06-29
It's hard to really say how easy or difficult it will be to accomplish what you want. But I am sure unix has the capability.

Might be worth looking at something like :

g4u - Harddisk Image Cloning for PCs
[http://www.feyrer.de/g4u/](http://www.feyrer.de/g4u/)

I am sure there are other similar tools around though.

---

### Post by Lunde on 2005-06-29
One option is to create a minimal boot CD or boot disk/s that can connect to the network, have a script to partitioning your drives and the grub installer, then CP -ax from the original full system over the network.

---

### Post by jeremy on 2005-06-30
I use partimage for this.

---

### Post by debian_n00b on 2005-06-30
Hey. My method for backing up is easy. It's how I used to do it on my Debian machines. Here is how to adapt it to a desktop machine. 

First off, you'll need at least 3 partitions on the drive. Swap, system and home partitions. It is imperitive that the home partition be larger, much larger, than the system partition. Lets say 10 gig system partition and the rest for home partition.

Next, we'll do a bit for bit copy of the system partition. And save on the home partition. Restoring is easy as 123.

To back up:
Code:

dd if=/dev/hda1 of=/dev/hda2/system_image.img


Simple as that. The file extension IMG is not necesary. I do it to remind myself what the file is. To restore, you just reverse the command.

Code:
dd if=/dev/hda2/system_image.img of=/dev/hda1


The IF and OF in the command represent "INPUT FILE" and OUTPUT FILE".

To backup a MBR, it's more or less the same, only you use a couple of extra switches at the end to tell the command dd to stop copying.

Code:

dd if=/dev/hda of=/home/user/mbr_backup bs=512 count=1


The BS option tells DD to copy 512 bytes at a time. The count tells DD to do this only once. Quick and dirty stuff. It results in only the fist sector, the MBR and partition table, getting coppied.

It's the first 446 bytes that is actually the MBR. The remaining 66 bytes is the partition table. So, if all you want is the MBR and not the table, replace 512 with 446.

As far as backing up personal data goes, well you don't **** around with that stuff. You burn it to cd regularily. And make multiple copies of the really important stuff.

After the image has been created and saved locally, it would be simple to store it on another machine on the network using either SAMBA or NFS. And it the system won;'t boot, then a Live Knoppix or Ubuntu disk could be used to boot and either restore the backup of the MBR and/or the system image from either the machiner locally or across the network.

---

