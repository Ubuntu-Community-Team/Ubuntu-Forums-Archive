---
title: "ext3 formatted usb hard drive not visible"
date: 2009-01-22
forum: Desktop Environments
---

### Post by shalamabobbi on 2009-01-22
I formatted a 500Gbyte hard drive with gparted as ext3. 
The formatted drive does not show up in the gui (places-computer)however.
Do I have to reboot before it will show up?
I'd rather not if possible, as I'm in the middle of downloading with emule.
Anything I am missing?

---

### Post by taurus on 2009-01-22
What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by deanjm1963 on 2009-01-22
If you've just formatted the drive, open up gparted again and hit Ctrl+R and that should refresh the new drive for you and it should appear on your desktop.

---

### Post by shalamabobbi on 2009-01-22
Thanks for the reply. I found a folder mnt where it showed up as being mounted but there was a folder called lost and found with the 'unreadable symbol associated with it. 

I used gparted again to unallocate the drive, then I unmounted it.

I next used a terminal and did the following:



bob@bob-desktop:~$ sudo mkfs.ext3 /dev/sdc1
mke2fs 1.41.3 (12-Oct-2008)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
30531584 inodes, 122096000 blocks
6104800 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=0
3727 block groups
32768 blocks per group, 32768 fragments per group
8192 inodes per group
Superblock backups stored on blocks: 
	32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
	4096000, 7962624, 11239424, 20480000, 23887872, 71663616, 78675968, 
	102400000

Writing inode tables: done                            
Creating journal (32768 blocks): done
Writing superblocks and filesystem accounting information: done

This filesystem will be automatically checked every 27 mounts or
180 days, whichever comes first.  Use tune2fs -c or -i to override.
bob@bob-desktop:~$ 

YOUR REQUESTED INFO

bob@bob-desktop:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xffdcf748

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9327    74919096   83  Linux
/dev/sda2            9328        9729     3229065    5  Extended
/dev/sda5            9328        9729     3229033+  82  Linux swap / Solaris

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x44fdfe06

   Device Boot      Start         End      Blocks   Id  System
bob@bob-desktop:~$ 


Now it shows up in the gui, but if I click on it I see a lost and found folder that has an unreadable designation and constitutes 435Gbytes of the disk??

---

### Post by deanjm1963 on 2009-01-22
first you need to give yourself ownwership and permissions of the drive

try

sudo chown -R <your username>:<your username> /media/disk
sudo chmod -R 755 /media/disk

then to remove allocated root space

sudo tune2fs -m 0 /dev/sdc1


no < > around your user name ... e.g. dean:dean

hope this helps

---

### Post by shalamabobbi on 2009-01-22
OK thanks. 

Now everything seems normal except I still see this 'lost and found' folder.
The size of the drive and the folder seem to coincide and it is readable.
Can I simply delete the folder? Where did it come from?

Last question.
If I plug in another external hard drive to format it for use with ubuntu, How do I properly take care of the ownership issue first so as to avoid an end run around?

Thanks.

---

### Post by deanjm1963 on 2009-01-22
the lost+found folder is part of ext3, every drive/partition formatted with ext2/3 has one.

you can only set permissions for a drive after you've formatted it, even if you've formatted it previously and changed ownership. all drives that have just been formatted are owned by root until you change it.

---

### Post by shalamabobbi on 2009-01-22
Glad I waited for your response then.
Thanks loads.

---

### Post by shalamabobbi on 2009-01-24
I finally located an article that proved useful in filling in the holes in my knowledge..


[http://www.smorgasbord.net/how-to-install-second-hard-drive-in-ubuntu-linux/](http://www.smorgasbord.net/how-to-install-second-hard-drive-in-ubuntu-linux/)

---

