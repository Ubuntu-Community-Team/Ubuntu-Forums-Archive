---
title: "Hardy Partition mounting nightmare!"
date: 2008-04-26
forum: Desktop Environments
---

### Post by BigSilly on 2008-04-26
Gah! It's sending me daft. When I used to use Gutsy, it listed automatically on the desktop which partitions I had available, and it mounted them without any intervention from me. But since doing a fresh install of Hardy, I can't get the system to automatically mount my 2 spare partitions. And worse yet, it seems to be renaming them itself and I don't know why.

I like to use SDLMame see, and I edit the mame.ini to point it at my spare partition where my roms are kept. I have to re-edit this now every time I reboot Ubuntu, because it's changing the partition name from 'disk' to 'disk-1' willy-nilly, and that's confusing my emulator. It's a real pain. Mounting manually wouldn't be so bad if I didn't have to faff around in text files every time I want to play a rom.

What can I do? If you need any more info please let me know, and thanks in advance.

---

### Post by Linja on 2008-04-26
You'll need to edit your /etc/fstab file. First run sudo fdisk -l to find out how those two partitions are identified. For example, if one is /dev/sda8, you would put this in your fstab:

/dev/sda8  /name_of_mountpoint   filetype(e.g. ext3)  noatime, nodiratime 0 0

The mountpoint must exist, of course. If not, you'll have to create it first. As for the noatime, nodiratime options, those apply only to linux native filesystems, if you have fat or ntfs, you'll have to use other options.

After editing your fstab, save it and run mount -a.
If you find that you are being denied access, run sudo chmod -R username.username /mountpoint on the folder.

---

### Post by BigSilly on 2008-04-26
Thanks very much for your reply. This is the fstab I currently have:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=ba248c94-a8b8-4bcb-858c-4df799dc7114 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=c7208c52-e601-11dc-bf2c-fbaa335115b0 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```

And this is the output of fdisk -l:

```
Disk /dev/sda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb1d0b1d0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4510    36226543+  83  Linux
/dev/sda2            4511        9964    43809255    f  W95 Ext'd (LBA)
/dev/sda5            4511        7197    21583296    b  W95 FAT32
/dev/sda6            7198        9827    21125443+  83  Linux
/dev/sda7            9828        9964     1100421   82  Linux swap / Solaris
```

I'm still a bit confused though; how come I never had this issue with Gutsy, or even Feisty? Still, thanks again for your response.

---

### Post by Linja on 2008-04-26
This should do, insert it just above the #sda7 line:

/dev/sda5   /home/username/FAT  vfat  rw,uid=1000,gid=1000,umask=0022   0 2
/dev/sda6   /home/username/OTHER ext3 relatime 0 2

You'll want to edit the names for the mountpoints I put int ("FAT" and "OTHER"). It's not very likely that you happen to have such folders in your home directory right now. Just use whatever names you like, like /home/your_username/Data or something. And as I suggested, you'll need to create folders with matching names manually before you try to mount anything (so, FAT and OTHER if you do simply copy over my example).

Hardy appears to have introduced a number of innovations into its installer. It doesn't pick up any other partitions anymore unless you tell it to (used to be the other way round). Here is some advice: /etc/fstab is one of the files that I always back up before I do a reinstall, then all you have to do is put it back once the system is up and running. That tend to save quite a bit of time and frustration.

---

### Post by BigSilly on 2008-04-26
Thankyou very much for your assistance. I'll get straight on to that.

The bit that's really confused me though, is why Ubuntu is renaming the partitions. I don't really mind having to manually mount a partition, but having to re-edit text files in emulators to point them at the constantly changing partition names is a real pain. They just keep swapping their names!

Still, I'm off to go and tinker with fstab. Thanks again. :)

---

