---
title: "Change to trash dir location"
date: 2010-07-15
forum: Desktop Environments
---

### Post by Veector on 2010-07-15
I have an SSD and i was wondering if i could change my trash location to an SD card that i always have plugged in, so that i write less to the drive and maybe extend the life of my ssd.

---

### Post by oOarthurOo on 2010-07-15
What desktop are you using?

Also, do you have xdg-user-dirs installed? That may not be its name on UBuntu, but it will be something similar.

"aptitude search xdg" should give you a pretty good match.

---

### Post by Veector on 2010-07-15
i'm using gnome

---

### Post by oOarthurOo on 2010-07-16
Are you sure this would save you writes? I mean, files aren't actually moved to the trash. A single bit is flipped, saying, it's trash. It's possible, though someone more familiar with these things will hopefully weigh in, but it's possible that moving the trash off would actually increase writes to the drive.

One alternative is to check the box in nautilus that enables the command to bypass trash altogether. 


Other places to look, that maybe offer more benefit for longevity of your drive:

Use a non-journalled file system for / and only journalled for home /ext 4. Put swap on the sd card. Add noatime to your fstab entries on each partition.

If you're committed to the trash idea, create the trash folder on your sd card. Make sure your user has permission to read/write to it. Delete the folder in ~/.local/trash ... I think that's where it is. Create a symlink from the sd card trash dir to the old trash location, e.g., ln -s /mount/sd/.user/trash /home/user/.local/trash

The real trick is with xdg... it has a conf file hidden that lets the system know where everything is. You can uninstall it, because it's really not that useful IMHO. Else you'll have to find it (try man xdg-user-dirs) and make sure it doesn't reference the /home/user/.local/trash location. Instead the new sd card one.

---

### Post by Veector on 2010-07-16
> Use a non-journalled file system for / and only journalled for home /ext 4. Put swap on the sd card. Add noatime to your fstab entries on each partition.

DO you know of a guide that would help me do this?

---

### Post by oOarthurOo on 2010-07-16
Could be very simple, depending on your setup. Why don't you post the output of fdisk -l and cat /etc/fstab for me.

---

### Post by Veector on 2010-07-16
victor@victor-laptop:~$ fdisk -l
victor@victor-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=69e62adf-f99b-4f95-ab21-46f90e961750 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=3aa7b792-195a-4caf-a4fb-9122d1fa08b1 none            swap    sw              0       0

---

### Post by oOarthurOo on 2010-07-16
heh... sorry, that's sudo fdisk -l   and that's a lowercase L. 

As for your fstab, bad news. You've got home and root on one partition, which means turning off journaling isn't really an option. However, we can still disable atime, which is when Ubuntu writes the last time files were accessed to the hard-drive. So long as you don't syncronize your files across different computers you won't miss it. We can also still move swap off your hard-drive onto the sd card, but for that we'll need the sudo fdisk -l output. 

Let's start with the easy change. Make your fstab look like this:
```
# / was on /dev/sda1 during installation
UUID=69e62adf-f99b-4f95-ab21-46f90e961750 / ext4 noatime,errors=remount-ro 0 1
```

That option will disable writing access times to the disk. 

Next, before we move your swap off... assuming you have 1GB or more of RAM, you can make this change as well. We want to edit the file"
```
/etc/systctl.conf
```
and add the line
```
vm.swappiness=0
```

You can read more about this [here]("http://ubuntuforums.org/showpost.php?p=1255511&postcount=43"), but in essense it just tells linux to use your ram rather than swapping out files to the disk. Important for you because of lifetime, rather than performance issues.

In case you haven't checked it out yet, you can add the option to nautilus to delete files directly. 

Go to >edit >preferences >behavior and you'll see the checkbox under the Trash options. Although I'm uncertain that moving trash off your disk would decrease writes, I think this might make a small, perhaps very small difference. less than the noatime option is my guess, but hey, every little bit right?

---

### Post by Veector on 2010-07-17
> victor@victor-laptop:~$  sudo fdisk -l
[sudo] password for victor: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000706e8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18663   149903360   83  Linux
/dev/sda2           18663       19458     6384641    5  Extended
/dev/sda5           18663       19458     6384640   82  Linux swap / Solaris

Disk /dev/sdb: 3963 MB, 3963617280 bytes
255 heads, 63 sectors/track, 481 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0
This is what i got, now i should do the /etc/systctl.conf thing?

---

### Post by linux18 on 2010-07-17
As the one familiar with this weighing in, ssd's are internally capable of wearing out the drive evenly ( so a small swap will be all over the disk mixed with all sorts of other files and constantly changing to lesser used parts of the disk ) the "wearing out" of ssd's is actually very slow even with swap ( win XP with swap on SSD's are still going years after the eee pc first came out ) my suggestion is try not to worry about wearing out the drive, they can handle several million R/W cycles before a single error..approximately 5 - 7 years.

You will probably have to reinstall before then at some point, in which case chose EXT2 as your filesystem.

If you have more than 768 MB of ram, won't do serious video editing, and usage never rises above 60 MB then you can get rid of swap all together.

---

### Post by oOarthurOo on 2010-07-17
Yeah, you can go ahead and add the vm.swappiness line to your /etc/sysctl.conf, that's a good thing to do. You have 1GB or more of RAM? If it's 512MB don't set it to 0, instead use 20.

Doing laundry now, but when I'm done I'll post how to move swap off onto /dev/sdb

---

### Post by Veector on 2010-07-17
Thank you so much

---

