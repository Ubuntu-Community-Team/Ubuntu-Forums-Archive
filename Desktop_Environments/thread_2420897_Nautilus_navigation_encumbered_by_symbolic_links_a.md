---
title: "Nautilus navigation encumbered by symbolic links and partitions"
date: 2019-06-12
forum: Desktop Environments
---

### Post by s-strickthrough on 2019-06-12
First post!

I've setup my computer a few ways.  First was simple with just Ubuntu 18.04, all of my data on the same partition as the OS and nautilus was quick everywhere.

My new system is dual boot with an ntfs shared partition.  The pertinent points of my new setup are:  Ubuntu 18.04 OS is on the root partition, my home folder is on an ext4 formatted partition (houses mostly the dot files), and my non-dot files are on the shared ntfs formatted partition.  For instance, the ~/Documents folder is a symbolic link to the corresponding Documents folder on the shared partition whereas my .config folder is on the ext4 formatted home partition.  My /etc/fstab file reads:

```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/nvme0n1p4 during installation
UUID=fb46f379-2bfa-46dc-bb14-b31db42d5b2c /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/nvme0n1p1 during installation
UUID=2A21-363D  /boot/efi       vfat    umask=0077      0       1
# /home was on /dev/nvme0n1p5 during installation
UUID=c57d851b-fde7-436a-8b76-3705cfaac690 /home           ext4    defaults        0       2
# /media/stephen/Lindows was on /dev/nvme0n1p6   New Addition
UUID=3AC0F7D6C0F795FB /media/stephen/Lindows              ntfs    defaults,umask=000,uid=1000,gid=1000        0       2
/swapfile                                 none            swap    sw              0       0

```

**The problem:**

When I use nautilus to navigate this sea of partitions and links, its performance is wildly inconsistent, unlike the way it was before the multiple partitions and symbolic links (the contents of the folders before and after the system changes are the same).

To give an example, if I click the files icon on the launcher, the home directory it brings up is slow to navigate (up/down buttons and expanding/descending into a directory) AND the cpu usage for the nautilus command maxes out the core it runs on for about 20 seconds for each navigation operation.  If instead, I go Other Locations -> Computer and then use the expandable folders, I can navigate (up down and expand a directory) in no time and with no cpu issues either (both folders on root and home and shared partitions).  The problem then continues that if I descend (not expand) into a folder on the root partition, navigation is smooth, but descending into any folder on the home partition is immediately sluggish with the same preceding issues.

It may be a connected issue but nautilus-desktop does the same king of cpu usage for the first 20-ish seconds after booting.

To be clear, this isn't an access issue to the partition.  I have used rsync to move 40G of data between the shared and home partitions in about 5 minutes.

Any help would be greatly appreciated!

---

### Post by oldfred on 2019-06-12
Since NVMe drive I would change fstab parameter from defaults to noatime, so not writing on every access.

But NTFS is somewhat slower with Linux as Linux developers have to figure out how to use it without help from Microsoft. And it uses the fuse layer which adds some overhead.

Also Windows periodically needs defrag and sometimes chkdsk. My old XP install booted in 5 minutes, but after a chkdsk booted in "only" 3 minutes when on that system Ubuntu booted in 40 sec.  You can only run chkdsk & defrag from Windows or a Windows repair disk.
NTFS partitions also slow down a lot if more than 70% full, so keep 30% free inside the NTFS partition.

       For ntfs UUID shown is example only see below:
UUID=XXXXXXXXXXX   /media/WinD ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0
Window_names prevents the use of invalid windows characters:
(which are the nine characters &#8221; * / : < > ? \ | and those whose code is less than 0×20) 
uid=1000 should fix the trash problems as well: 

Have you updated firmware for NVMe drive? Many also need that to work or improve performance.
      
 Do SSD need customization?
[http://ubuntuforums.org/showthread.php?t=1981478](http://ubuntuforums.org/showthread.php?t=1981478)
[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)
[https://wiki.debian.org/SSDOptimization](https://wiki.debian.org/SSDOptimization)
[http://ubuntuforums.org/showthread.php?t=2003022](http://ubuntuforums.org/showthread.php?t=2003022)

---

### Post by s-strickthrough on 2019-06-12
Thanks for the quick reply.  I have a bit of reading still to do about optimizing up my SSD.

You make a clear case as to why NTFS is a bad choice for linux, but I am still confused as to why NTFS would be fast to access through expanding folders starting at root and slow to access by descending through folder.  Why wouldn't it be slow to access in all situations?  Also, why would my dot folder (located on the Ext4 partition) also be slow to descend into?

Also, if I need to have a partition that windows and ubuntu can both easily access, is there a better file system choice?  I'm discounting ExtX as the Ext2Fsd utility often recommended did not work for accessing my Ext4 partition as advertised.

---

### Post by oldfred on 2019-06-12
Do you have noatime parameter on all your mounts in fstab?
I use relatime for my HDD partition mounts. See:
man mount

I do not think You can access SSD without AHCI, but is that on in UEFI settings?

---

### Post by s-strickthrough on 2019-06-12
I haven't yet changed my fstab since I'm still reading.  The mounting is still done with defaults (looks like relatime is the default).

I do have AHCI configured for the SATA settings in the UEFI.

I'm also struggling to see how changing the recording of inode access times will speed up nautilus.

---

### Post by oldfred on 2019-06-12
Speeds up since every access has to have a write to update access time. But with noatime that is not written by default. May break a few apps like mutt that depend on access times. I have changed it and every site on SSD settings recommends noatime.

---

### Post by s-strickthrough on 2019-06-12
I fixed the problem.  I don't know why this worked, but it was something that I had done and had not mentioned.

Because I had symbolically linked all of my non-dot directories to my ntfs partition, I had also changed the .config/user-dirs.dirs file so that the standard directories (e.g. Documents, Downloads, etc.) were located in the ntfs partition.  See [https://askubuntu.com/questions/67044/change-default-user-folders-path](https://askubuntu.com/questions/67044/change-default-user-folders-path).

Upon reverting the .config/user-dirs.dirs folder (undoing everything described in the link), nautilus went back to working smoothly.

---

