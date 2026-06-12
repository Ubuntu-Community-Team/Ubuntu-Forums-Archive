---
title: "Completely Format a pen drive"
date: 2008-12-14
forum: General Help
---

### Post by daz4126 on 2008-12-14
I've got a 8gb cruzer pen drive and it has some rubbishy software that auto-loads on windows machines. I tried formatting the drive using gParted, but it still loads this software, so I guess it must be on some sort of hidden partition. Is there any software on Ubuntu that can completely wipe a drive ... I just want it as a blank drive!

cheers,

DAZ

---

### Post by SuperSonic4 on 2008-12-14
It sounds more like a firmware issue than a formatting issue. Did you delete the partition then reformat in gparted?

---

### Post by caljohnsmith on 2008-12-14
You could zero-out the first track on the drive which includes the MBR (Master Boot Record) on the pen drive by doing:
```
sudo dd if=/dev/zero of=/dev/sdX count=63
```
And replace "sdX" with the pen drive. If that doesn't work, how about posting:
```
sudo fdisk -lu
```
And we can work from there if you want.

---

### Post by hrod beraht on 2008-12-14
**Step 1: delete the previous partitions**

For that you can use fdisk:

```
sudo fdisk /dev/<your_device>
```

Note: enter m for the help

**Step 2: create the new file system**

To format with a FAT (DOS/Windows) file system (which will work with Windows or Linux machines):
```
sudo mkfs.vfat /dev/<your_device>
```

To format with a Linux ext3 file system:
```
sudo mkfs.ext3 /dev/<your_device>
```

**Step 3: check**

Now you can check the new file system with fsck:

```
sudo fsck /dev/<your_device>
```

That's it ! 

Bob

---

### Post by tuskenraider on 2008-12-14
i had a drive like that... it was the biggest peice of rubbish... anyway... idk if you have windoze but i had to go to [http://www.u3.com/](http://www.u3.com/) and download the uninstaller there.  Idk if i thought about formatting it.. but as im sitting here.. the uninstaller was the only thing that worked.... that i can remember.

good luck..

tusken

---

### Post by daz4126 on 2008-12-14
Thanks for all the replies guys. Here's what I've done so far:
* Gone into gParted and deleted the partition, then added a new one formatted as fat32
* applied the code given by caljohnsmith to zero out the mbr.
* Here are the results of sudo fdisk -lu:

Disk /dev/sdb: 8029 MB, 8029470208 bytes
255 heads, 63 sectors/track, 976 cylinders, total 15682559 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000e8c2e

Put it into a windows machine and it booted up the crappy u3 software.

On the u3 webpage that tusken referred to it says that you can uninstall it from within the program itself, so I'm off to try that. Failing that, is it possible to zero the whole drive?

thanks again,

DAZ

---

### Post by caljohnsmith on 2008-12-14
I think maybe your pen drive is not what is causing the U3 software to load at this point. If you want to zero the whole drive, simply do:
```
sudo dd if=/dev/zero of=/dev/sdX
```
And then every byte on the drive sdX will be zeroed (replace sdX with the drive again). Maybe that will solve your problem, but I would be suprised since you all ready zeroed the MBR and deleted the partitions.

---

### Post by daz4126 on 2008-12-14
Turned out there was an option to get rid of the software on the stick itself - it's gone now, thank you so much for the help everyone - all of the command-line stuff is always useful to know.

cheers,

DAZ

---

### Post by AlexFoster on 2008-12-15
I'm trying to format an 8GB cruser micro in order to make it into a bootable pen drive (for the new eeebuntu).

I have formatted it to ext2 but when I: 
```
sudo ./isotostick.sh /eeebunutu-2.0-base.iso /dev/sdc1
```

It says the partition isn't bootable (I ticked the flag for it to be bootable in gparted, but oh well). To make it bootable it says to: ```
# /sbin/parted /dev//
/dev/sdc1 toggle N boot
```

When I do ```
/dev/sdc1 toggle N boot
``` I get:
```
bash: /dev/sdc1: Permission denied
```

I've tried doing a complete reformat using the advice in this thread but I've hit this rather frustrating road block.

---

### Post by yogo on 2008-12-15
pendrive linux has excellent tutorials for formating pendrives etc.

---

### Post by caljohnsmith on 2008-12-15
Rather than use "parted" to mark the partition bootable, I think an easier way would be to run the command:
```
sudo sfdisk -A1 /dev/sdc

```
That will mark the first partition on the sdc drive as bootable. How about giving that shot and let me know how it goes.

---

### Post by AlexFoster on 2008-12-15
I ran that and it said: Done

Then I did:
```
sudo /home/user/isotostick.sh /home/user/eeebuntu-2.0-base.iso /dev/sdc1
```

This is what I get:

```
Not verifying image...(no checkisomd5 in Ubuntu so skipping)!
no record for 'sdc1' in database
Partition isn't marked bootable!
You can mark the partition as bootable with
    # /sbin/parted /dev//
    (parted) toggle N boot
    (parted) quit
Cleaning up to exit...
```

---

