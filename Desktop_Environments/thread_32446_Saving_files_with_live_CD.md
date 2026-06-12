---
title: "Saving files with live CD"
date: 2005-05-07
forum: Desktop Environments
---

### Post by falconeye on 2005-05-07
Hi, 

It is the first time I am using ubuntu (I am only using Live CD). I am sorry if my question is stupid (I am a newbie in linux), but I would like to know how to save files on a USB key for example when I am using the live CD ? 

Can you please also tell me how to save it on a floppy disk ? If it is possible to save it also on the hard disk, it would be great, but I think it is not possible. 

I don't want to install ubuntu on my Hard disk, but only find a solution to save files and even configurations. It would be so great if I could using Ubuntu as a true OS without installing it.

Thanks in advance,

Best regards,

---

### Post by enquiry on 2005-05-07
Before you can write files to a filesystem, it must be mounted. A USB key will usually get mounted automatically.

To mount a floppy, just put the floppy in, go to Places -> Computer, right click on the Floppy icon and choose Mount Volume.

To mount a hard disk partition, you must first create a folder to mount it on. Such a mount point is usually in /mnt. Open a terminal and write:
```
sudo mkdir /mnt/mountpoint
``` Here I'm naming the folder mountpoint, but you can name it whatever you want.
Then mount the partition:
```
sudo mount /dev/hda1 /mnt/mountpoint
``` (hda1 is just an example, for a list of available partitions, type sudo fdisk -l). 

This will only work with filesystems supported by Linux (like fat32). You can mount NTFS partitions, but you can't write to them. If you use NTFS, you can create a fat32 partition that can be accessed under both Linux and Windows.

---

### Post by falconeye on 2005-05-07
ok, thanks a lot.

Is it possible to save a configuration. For example if I create folders with files, can I save all directories on an usb device and retore automaticaly these saved files and configuration in order to have linux restored as It was before I switch off my computer ?

May be I am asking a lot from Ubuntu  :???:

---

### Post by enquiry on 2005-05-07
I don't belive the Ubuntu LiveCD has this feature (saving configurations). I know Knoppix have it though.

---

### Post by Ptero-4 on 2005-05-07
[QUOTE=enquiry]I don't belive the Ubuntu LiveCD has this feature (saving configurations). I know Knoppix have it though.[/QUOTE]
 Ubuntu AFAIK don't do that, KNOPPIX have what they call "persistant home", this means that your home folder (with your configurations) is stored in a special "partition" which is stored as a regular file in an existing partition in your HD (usually s FAT/FAT32 partition).

---

