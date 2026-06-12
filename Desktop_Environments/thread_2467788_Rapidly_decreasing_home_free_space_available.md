---
title: "Rapidly decreasing home free space available"
date: 2021-10-07
forum: Desktop Environments
---

### Post by cAlpha on 2021-10-07
At startup, I have ~1G available in my home directory.  

Occasionally, I'll get Ubuntu warning messages that I have XXXM space remaining.  For instance, ATM:
```
chris@chris-x1c6:~$ mydf
Filesystem      Size  Used Avail Use% Mounted on
udev            7.7G     0  7.7G   0% /dev
tmpfs           1.6G  5.5M  1.6G   1% /run
/dev/nvme0n1p5   40G   38G   75M 100% /
tmpfs           7.8G  8.0K  7.8G   1% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           7.8G     0  7.8G   0% /sys/fs/cgroup
/dev/nvme0n1p4   50G   12G   39G  24% /media/Share
/dev/nvme0n1p1  256M   34M  223M  13% /boot/efi
tmpfs           1.6G   16K  1.6G   1% /run/user/121
tmpfs           1.6G   44K  1.6G   1% /run/user/1000
```

Can anyone provide suggestions for debugging and resolving this.  Many thanks

---

### Post by TheFu on 2021-10-07
```
/dev/nvme0n1p5   40G   38G   75M 100% /
```
is the only storage that matters.  The tmpfs are virtual file systems and safely ignored.

For most normal users, 35G is needed just for the 20.04 and later OSes. That doesn't include space for /home/.
If the partition is filling up, delete some files. Clean up some old programs and old data and consider adding another partition for the /home/ to have HOME and the OS separate.  Also, you can clean up cache files and extra snap versions.

So, how to all of this?
Start with the easy stuff.
```
sudo apt autoremove
sudo apt autoclean
```

Here's a script to clean up old snap packages:
$ more ~/bin/snap-remove-disabled
```
#!/bin/sh
set -eu

snap list --all | awk '/disabled/{print $1, $3}' |
    while read snapname revision; do
    sudo snap remove "$snapname" --revision="$revision"
    done

```
Run those and see if that helps.
I don't think any of those commands can do any harm.

---

### Post by cAlpha on 2021-10-07
Thanks, that opened up about 170M.

Speaking of, I'd originally created the partition with 40GB since it seemed like way more than I'd need.  I was ablet to resize my main partition to open up about 140G of space, but it isn't adjacent to the drive in question (I have another partition that sits between it that I've formatted to be used for common storage for each).  

[IMG]https://i.imgur.com/xRi1YVw.jpg[/IMG]

Any way to use this to extend my existing Ubuntu partition

---

### Post by Dennis N on 2021-10-07
> **cAlpha said:**
> Any way to use this to extend my existing Ubuntu partition 
You could create a new ext4 partition in the unallocated space, and mount it somewhere in Ubuntu's file system to use as additional place to keep some of your files. In that way, you could "extend" your space.

---

### Post by cAlpha on 2021-10-08
> **Dennis N said:**
> You could create a new ext4 partition in the unallocated space, and mount it somewhere in Ubuntu's file system to use as additional place to keep some of your files. In that way, you could "extend" your space.

Not looking for another place to keep files, looking for extra space for the base Ubuntu installation.

---

### Post by Dennis N on 2021-10-08
> **cAlpha said:**
> Not looking for another place to keep files, looking for extra space for the base Ubuntu installation.

You'd have to move partition 4 and 5 to the left to adjoin partition 3. Then you could expand partition 5 to the right. gparted has a resize/move operation for partitions that may be what you are looking for. Be sure to back up any important data if you use that. I think it's a risky operation.

_Added Comment_
if you understand LVM and are willing to reinstall Ubuntu, you could create a new partition in the current unallocated space, then create a volume group out of this new partition and partition 5. Then install Ubuntu on a logical volume in that volume group. That logical volume can then use space in both partitions.

---

### Post by ActionParsnip on 2021-10-08
What is the output of:
```

cd /; sudo du -sh *

```
Thanks

---

### Post by TheFu on 2021-10-08
> **cAlpha said:**
> Not looking for another place to keep files, looking for extra space for the base Ubuntu installation.

First - I don't know if you were just lucky or made a smart choice, but excellent that the HDD partitioning is using GPT.  That provides options and simplifies things that the old 1984 MBR/MSDOS partitioning method would vastly complicate. MSDOS partitioning almost always means dealing with Logical Partitions inside an Extended Partition. With GPT that stuff doesn't exist and we can simply create partitions - I think 128 are allowed. This can be very handy.

There are lots of options, but none are easy or without great risk.
Shifting a partition has risks and takes a very long time.  I did it once and would never, ever, ever, do it again.
If you had installed with LVM (it is a checkbox in most installers), making use of the extra storage wouldn't be very hard.  LVM == Logical Volume Management.  You can look what it can do up on wikipedia or 500 different websites. It is more complex than "simple partitions."  Also, at install time, it takes expert level control to setup on a dual-boot system.  

The way that I deal with dual-boot - is that I don't.  I put Windows inside a virtual machine and let the more advanced OS control all the hardware.

There are other options too.  Like you could probably copy the 40G partition into the start of the 140G space, then setup the boot stuff to point to that other partition and delete the old 40G partition.  That will oddly be faster than shifting, but it will entail manually doing some things that the installers handle automatically. Expect to manually edit the /etc/fstab file.  It isn't hard, but it is extremely detailed work. If you get anything wrong in doing that, *forgetaboutit*.

What I would do is 2 things.
0) Create a full backup of everything on the system that you cannot lose. This is all very dangerous stuff.
1) Create 3 new partitions from the start of the free space. Use gparted. Give each a unique LABEL.  UNUSED01, SWAP01, HOME01
2) The first will be a placeholder that we'll delete when done.  Make it 20G. It will be emergency space that your Windows can grow into if you out grow it, just a little. Expanding to the "right" is easy. Expanding to the "left" is very, very, hard. This 20G will be a little reminder that you need to buy a new HDD, should you expand into it. **Do not** format it.
3) Remove the swap file from the main Linux partition (swapoff) and create a swap partition - 4.1G in size. Put that in the unused space, far "left" after the 20G free space. You can look up how to accomplish that.  Format it as "**Linux Swap**" - LABEL = SWAP01
4) Create a new partition to hold /home. Make it the size you think you'll need, but do not allocate all the space.  Leave room to grow to the "right."  Maybe start with 30G.  Format it as **ext4**.  - LABEL = HOME01

After changing all this, reboot and see the new "names" for the partitions. If you can, reboot into a Try Ubuntu  environment off a flash USB drive. This will make things easier for the next steps.  Ubuntu, Xubuntu, Lubuntu, ... whatever ... it doesn't matter.  Just make it the same release that you have installed.

The next steps are to tell the Ubuntu OS where this new storage is, how to mount it (/etc/fstab) and copy files from the OLD /home over to the new /home/ while both are mounted to .... somewhere else.  I'd create 2 directories - /mnt/old  and /mnt/new, then mount the old / to /mnt/old   and the new 30G partition we created above as ext4, to /mnt/new.  Then I'd use **sudo mv /mnt/old/home/* /mnt/new/**  Note the exact levels of the FROM and TO commands.  The mv command is destructive, so if you get it wrong (or I made a mistake), it won't be good. You cannot use a GUI and copy/paste stuff. That will break things and doesn't provide the control over details that is needed.  

After that move is done, we need to mount the home and swap partitions.  It would be smart to use either a LABEL= or UUID= instead of the device name.  Use the **blkid** command to get the mapping between the device name and the LABEL/UUID.  Remember those labels we put on each partition?  Those will come in handy now.  Labels are must easier for humans than UUIDs. You can use either, as you like. Having a label on a partition doesn't prevent using UUIDs.

I'd verify that the /mnt/old/etc/fstab file is correct for the new storage and new swap partition.  
A new line will be needed to mount /home partition onto /home.  
```
LABEL=HOME01  /home ext4   noatime,errors=remount-ro 0 1
```
For the swap, you'll change from a swap file line ... probably something like /swapfile ---> the new 4.1G swap partition ...  /dev/nvme0n1p8?  I don't know the actual device.  
```
LABEL=SWAP01  none    swap   sw      0       0
```
Don't forget to  delete the unused swapfile. Since we deleted that line in the /etc/fstab file, deleting it now or after reboot isn't hard.

In theory, that should be it.  Reboot into the Ubuntu, not using the flash drive.  Label's are cool. Just know they have to be unique for any storage ever connected to the system. To see a label for a partition (or other file system object), use:
```
lsblk -e 7 -o name,size,type,fstype,[COLOR="#FF0000"]label[/COLOR],mountpoint
```
There are other ways, but this is very handy.

It takes much more to write this out than it takes to actually do the task.
What you've done is used about 60G of space in the 140G unallocated area. The new HOME01 area can be expanded to-the-right easily using gparted in the future, if needed.
You've switched from using a swapfile to using a swap partition. 4.1G is probably the best size for a swap file on a desktop Linux. You cannot hibernate if you have more RAM, but if you've gone to the effort to use encryption for data, then you don't want to use hibernation anyways.  Standby mode still works, btw.
And we freed up the space in the old OS partition used by both the swap and /home files.  That should be 10G or more.  If you autoremove and autoclean and remove unused snaps, the amount of storage there should be fine for years.

Here's my 20.04 desktop:
```
$ dft
Filesystem                 Type  Size  Used Avail Use% Mounted on
/dev/mapper/vgubuntu--root ext4   19G   11G  7.2G  60% /
/dev/mapper/vgubuntu--home ext4   12G  6.8G  4.4G  61% /home

```
Note the used sizes.

I use LVM, so don't worry about the first column too much.  I'm running a minimal install and don't install 50 different bloated GUI programs on it. You can't see it, but those allocations are actually split across 2 SSDs.  1 is 30G and the other is 10G.  I was caught running out of space just like you. Thanks to LVM, I was able to expand the / (root) logical volume into the 2nd disk.  I left home where it was. I would never allow an LV to span across physical devices ... and I haven't here either.  Both the disks are virtual and come from the same physical SSD.

---

### Post by cAlpha on 2021-10-08
> **ActionParsnip said:**
> What is the output of:
```

cd /; sudo du -sh *

```
Thanks

```
chris@chris-x1c6:/$ sudo du -sh *
17M	bin
151M	boot
4.0K	cdrom
26M	chris
8.0K	dev
4.0K	E
18M	etc
15G	home
0	initrd.img
0	initrd.img.old
948M	lib
5.8M	lib32
4.0K	lib64
16K	lost+found
4.2T	media
4.0K	mnt
474M	opt
du: cannot access 'proc/4071/task/4071/fd/4': No such file or directory
du: cannot access 'proc/4071/task/4071/fdinfo/4': No such file or directory
du: cannot access 'proc/4071/fd/3': No such file or directory
du: cannot access 'proc/4071/fdinfo/3': No such file or directory
0	proc
1.3M	root
du: cannot access 'run/user/1000/gvfs': Permission denied
4.7M	run
15M	sbin
14G	snap
8.0K	srv
0	sys
148K	tmp
9.6G	usr
9.1G	var
0	vmlinuz
0	vmlinuz.old
```

---

### Post by cAlpha on 2021-10-08
> **TheFu said:**
> 

...

I use LVM, so don't worry about the first column too much.  I'm running a minimal install and don't install 50 different bloated GUI programs on it. You can't see it, but those allocations are actually split across 2 SSDs.  1 is 30G and the other is 10G.  I was caught running out of space just like you. Thanks to LVM, I was able to expand the / (root) logical volume into the 2nd disk.  I left home where it was. I would never allow an LV to span across physical devices ... and I haven't here either.  Both the disks are virtual and come from the same physical SSD.

Thanks for the thorough reply.  

Part of me had considered, aside from moving partitions, that the easiest way to deal with this might just be to:

(1) save all of my configuration files and the 'Share' partition files onto a connected external drive
(2) wipe the existing partitions
(3) incorporate back into the Windows partition
(4) recreate the Share and Ubuntu partitions again, this time sizing more appropriately
(5) reinstall Ubuntu and replace backed up Share files onto new Share partition

Any reason this would be less desirable than what you're describing?

---

### Post by TheFu on 2021-10-08
So ... first it would be good to sort the output.  That's easy.
```
$ sudo du -sh * | sort -h
0       initrd.img
0       initrd.img.old
0       proc
0       sys
0       vmlinuz
0       vmlinuz.old
du: cannot access 'proc/4071/fd/3': No such file or directory
du: cannot access 'proc/4071/fdinfo/3': No such file or directory
du: cannot access 'proc/4071/task/4071/fd/4': No such file or directory
du: cannot access 'proc/4071/task/4071/fdinfo/4': No such file or directory
du: cannot access 'run/user/1000/gvfs': Permission denied
4.0K    cdrom
4.0K    E
4.0K    lib64
4.0K    mnt
8.0K    dev
8.0K    srv
16K     lost+found
148K    tmp
1.3M    root
4.7M    run
5.8M    lib32
15M     sbin
17M     bin
18M     etc
26M     chris
151M    boot
[B]474M    opt
948M    lib
9.1G    var
9.6G    usr
14G     snap
15G     home
4.2T    media
[/B]
```
So ... now we can look just at the bottom few lines and ignore all the others.  Going back to  the df output:
```
$ mydf
Filesystem      Size  Used Avail Use% Mounted on
/dev/nvme0n1p5   40G   38G   75M 100% /
/dev/nvme0n1p4   50G   12G   39G  24% /media/Share
/dev/nvme0n1p1  256M   34M  223M  13% /boot/efi

```
So /media is on a different file system.  Not important.
That leaves /home, /snap,  and OS stuff. You can control what goes into those two.
Almost always, you can choose NOT to use bloated snap programs.  Find the standard install and stop using "Ubuntu Software Center" to load snaps.  There are very view snap-package-only programs and even those have alternatives almost always that aren't snaps.

The solution for /home is what my last post explained.

---

### Post by TheFu on 2021-10-08
> **cAlpha said:**
>  Any reason this would be less desirable than what you're describing?

I cannot say. There are many complications on each system and what 1 person considers "desirable" isn't necessarily what another person would.  Just copying files loses 50% of the information that Linux needs about each file for a proper restore.  For plain data, that may not be important.  For non-data files, it could be absolutely critical. I know which files it matters on my systems, but couldn't presume to know what your system has.

The safe answer is ... don't expect a simple copy to work. Get the metadata on each file too. A simple copy almost always loses the metadata that we need when restoring to another install.  Anything outside your HOME directory is likely to need that metadata and a few files inside your HOME have extremely specific settings that will break programs if not maintained. A copy using a GUI doesn't keep that metadata.  Use backup tool - or use cp/rsync with the specific options to maintain the metadata.  BTW, of the target location for that copy isn't a native Linux file system, the metadata will be lost too.

---

### Post by ActionParsnip on 2021-10-09
You have 9Gb in /var
If you run
```

cd /var
sudo du -sh *

```
Then you can see what is taking up the space. Rinse and repeat until you have interrogated the file system and you can see what is taking up the space.

---

### Post by yancek on 2021-10-10
>  I'd originally created the partition with 40GB since it seemed like way more than I'd need.  

It should be if we're referring to a system partition.  Any recommendations you see as to the size needed for an Ubuntu or Linux install is for the system and software.  There is no way to know what size will be needed for data as that depends on what the user needs.  Text files take up very little space while audio and image files take up a lot of space.  So my point is that 40GB is more than enough for your Ubuntu system, but is severely lacking for data.  This is one of the primary reasons many users create a separate /home partition.

I'd agree that you should take a look at /var since it is likely that much of that 9GB is going to be in /var/log and you can delete files there without problem.  You might keep the newest of each and delete the older files.  Should knock that 9GB down considerably.

---

### Post by TheFu on 2021-10-10
> **ActionParsnip said:**
> You have 9Gb in /var
If you run
```

cd /var
sudo du -sh *

```
Then you can see what is taking up the space. Rinse and repeat until you have interrogated the file system and you can see what is taking up the space.

I posted a tedious example of doing this 1-2 months ago for someone else who had unexpected storage used.  [https://ubuntuforums.org/showthread.php?t=2467111&p=14059347#post14059347](https://ubuntuforums.org/showthread.php?t=2467111&p=14059347#post14059347) It has **du** and **find** examples.  It found stuff in unexpected places.

---

