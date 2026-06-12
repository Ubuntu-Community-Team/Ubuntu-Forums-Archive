---
title: "after xubuntu 20.04 install remove unused mount points"
date: 2020-09-28
forum: Desktop Environments
---

### Post by lou6 on 2020-09-28
I recently installed xubuntu 20.04 but the install left 2 unused mount points on my desktop.  I tried "sudo rmdir /media/lou/'mount point name' with no joy - when the mount point was unmounted it was not found and when it was mounted (and empty) it was busy.  These items are doing no harm but are cluttering my desktop.  How can I remove them?

EDIT: further research tells me that the mount points are in the /etc/fstab file and must be edited out - I don't feel up to that job (still noobish after several years as a Linux user) and would really appreciate some help...

---

### Post by metacell on 2020-09-29
@lou6, that's easy. Just do

```
sudo pico /etc/fstab
```

... and put a # in front of the two lines with the mount points.

Then press Ctrl-x to exit the editor, press y when it asks you to save, and press Enter to confirm the filename.

# is used to make a line into a comment. You only need to be careful to comment out the right two lines.

---

### Post by lou6 on 2020-09-29
Tried that and xubuntu failed to boot (/swapfile missing, although I DEFINITELY did not comment out the swapfile entry - not that much of a noob!).  I reinstalled xubuntu 20/04 LTS and now have four mount point artifacts on my desktop.  I've installed xubuntu from dvd several times since 2014 and have never had a problem like this before.

---

### Post by lou6 on 2020-09-29
Tried once again to remove the unnecessary mount points without success - had to reinstall yet again after another failure.  I'm still hoping for help to remove these items...I now have 5 useless mount points on my desktop.

Thanks in advance for help...

---

### Post by CelticWarrior on 2020-09-29
Are you doing a fresh reinstall? Or are you selecting some option to install side by side?

---

### Post by lou6 on 2020-09-29
I'm doing a fresh reinstall each time as I try various ways to remove the mount point icons.  When I fail, xubuntu won't boot and I must reinstall. I would post a .jpg of my desktop but don't know how.  Each mount point appears as a hard drive symbol (a rectangular box) with text below that says "537 MB volume" or "538 MB volume". When clicked they open a box that says "folder is empty".  When right-clicked, they unmount but the icon remains on the desktop. There is no option to delete them.  Each time I reinstall a new icon is added.

---

### Post by TheFu on 2020-09-29
post the contents of the fstab, please.

btw, use **sudoedit** to edit system files. That is the safest method.

---

### Post by lou6 on 2020-09-29
fstab looks normal to me now (since I just reinstalled and system is running properly). Problem is, how to get rid of the strange icons.  Or, I can just ignore them... 

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda8 during installation
UUID=23ddbab0-e1eb-4ff3-8c66-29a444090b60 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda7 during installation
UUID=6CB1-5EBF  /boot/efi       vfat    umask=0077      0       1
/swapfile                                 none            swap    sw              0       0

I've been using nautilus-admin to edit system files since gksudo died.

---

### Post by lou6 on 2020-09-30
This morning when I booted up I had nothing on my desktop except the top panel - no folders or icons anywhere on the desktop.  My wife's screen was normal and working properly.  This happened once before in my six installs of 20.04.

I reinstalled xubuntu 18.04 (which had run fine for years).  Strangely enough, the six useless icons (537 MB Volume) are still on the desktop.

I'll stick with 18.04 and see what develops with 20.04.  Rebuilding my system from scratch takes from 1.5 to 2 hours and I can't do this every day (or sometimes more than once a day).

Thanks in advance for any future help...

---

### Post by TheFu on 2020-09-30
issue is unrelated to fstab.  100% gui problem.  to troubleshoot gui stuff, create a new user account and see if the problem happens in that account too.  If not, then it is specific to 1 user account settings. Those are stored in the HOME.

---

### Post by lou6 on 2020-09-30
created a test user.  the questionable icons are not on that desktop but do appear on both my desktop and my wife's.  is there a way to remove the icons from our desktops?

thanks for your prompt reply to my predicament

---

### Post by CelticWarrior on 2020-09-30
Have you kept /home between installation? If so they can be remnants

---

### Post by lou6 on 2020-09-30
I don't have a separate home folder (if that is what you mean).  As far as I know, the entire system is reinstalled.  I'm sorry - I guess I don't understand the question.  If I had kept /home how would I have done it?

When I reinstalled I checked the first option (replace existing install).

---

### Post by ajgreeny on 2020-09-30
I am a bit baffled by all this but so far, unless I've missed it, nobody has asked you either to show us a screenshot of your desktop with these two mountpoints showing (what do they show as, and how do you know they're mountpoints?) or to show us the output of command```
ls -la Desktop
```
Both of these might give us a clue.
Alternatively you could just set your desktop to not show any icons by right clicking and choosing Desktop Settings -> Icons tab.  You can choose to keep some types if you wish, or hide everything.

---

### Post by lou6 on 2020-09-30
lou@lou-Latitude-E6420:~$ ls -la Desktop
total 8
drwxr-xr-x  2 lou lou 4096 Sep 30 07:44 .
drwxr-xr-x 16 lou lou 4096 Sep 30 10:35 

If it's any help, when I double click any of those icons they mount an empty file in /media/lou
 tried to post a screenshot with no success, but I'm up to 7 extra icons now...

---

### Post by lou6 on 2020-09-30
I mounted one of the 6 mount points (A036-A9F3) and did a catfish search.  Found in;

/dev/disk/by-uuid
/run/udev/links


On another note, I was notified today of availability of 20.04 LTS upgrade.  Under the circumstances (7 reinstalls, all more or less unsucessful) should I try upgrading my brand new 18.04?

---

### Post by ajgreeny on 2020-09-30
Did I misunderstand you when you said there were unused mount-points on your desktop?

I presumed you were seeing some icons or something on the Desktop of your system but perhaps there is nothing showing on the Desktop?
There are certainly no files of any sort in your Desktop folder which, depending on your settings, might show as icons on the Desktop.

---

### Post by TheFu on 2020-09-30
Everything under /dev/disk/ is created as disks/partitions are found by the kernel. The symbolic links are only for use as mounts, but don't mount anything.  Look at where the UUID points (use **ls -l**) ... it points to the device-mapper or partition only. There are others in the by-label/ and other subdirectories under /dev/disk/. Inside enterprises, these other links are commonly used rather than the UUID links.

/run/udev/links are for USB and other udev known devices. Again, they aren't mounted, just there for other subsystems to use.

Should you move to 20.04?  Probably, but not definitely.  Whether you should attempt to upgrade in-place or not depends on all sorts of things, how clean the prior installs were is a chief consideration.  OTOH, if you haven't used any PPAs, haven't manually installed **any** .deb files and have just been using Canonical software management tools all this time, then it will probably go ok. Nothing is guaranteed.  Most of my "upgrades" work fine, then just need some tweaks for specific server configs that have changed.  

On systems where I haven't been so clean with package management, I won't even bother trying and will just do a fresh install, then restore my configs and data from normal backups.  For these systems, I'll plan on about 3-5 attempts being necessary before I get it working well.  For example, my email gateway is called "spam3". There have been spam1 & spam2 before. Guess which one worked?  Until I'd tested everything, I didn't switch external connections from the old server to the new one.  I'm cautious that way.  I'll probably need to do a fresh install for the next email gateway too. It is running debian and giving me some network config problems the last few weeks that were never any issue before - the last 8 yrs.  Clearly, something has changed, somewhere, in the debian network stack.

Before attempting any OS upgrade, always have a know-you-can-restore backup or 20.  My systems have at least 90 days of versioned backups. That email gateway server has 180 days because it is a high-risk system, constantly attacked.  Constantly is being nice. Every few seconds, there are 20-100 attacks.

---

### Post by lou6 on 2020-09-30
ajgreeny - not to be disagreeable but they are definitely mount points - when double-clicked they mount an empty 537 MB Volume and display a hard drive logo.  A couple of posts back I did a search for one by its mounted label and posted the results. 

I mounted one of the 6 mount points (A036-A9F3) and did a catfish search.  Found in;

/dev/disk/by-uuid
/run/udev/links


What they are needed for and why they are on the desktop is the question.

See attached:

Thanks

---

### Post by scorp123 on 2020-09-30
> **lou6 said:**
> I recently installed xubuntu 20.04 but the install left 2 unused mount points on my desktop.  I tried "sudo rmdir /media/lou/'mount point name' with no joy - when the mount point was unmounted it was not found and when it was mounted (and empty) it was busy.  These items are doing no harm but are cluttering my desktop.  How can I remove them?

EDIT: further research tells me that the mount points are in the /etc/fstab file and must be edited out - I don't feel up to that job (still noobish after several years as a Linux user) and would really appreciate some help...

If they are indeed shown as disk icons as you said in one of your posts, they should be visible as partitions... no?  Can you please click on them, so that they are mounted, and then give us the output of these commands:

```
mount
sudo fdisk -l

```

These commands should spit out a list of all things that were somehow somewhere mounted by the system and also a list of all disk partitions that the system knows about. If there are any "mystery mount points" they should show up here in these command outputs. That would help to determine the cause and the next steps we need to take.

---

### Post by lou6 on 2020-09-30
scorp123;

lou@lou-Latitude-E6420:~$ mount
sysfs on /sys type sysfs (rw,nosuid,nodev,noexec,relatime)
proc on /proc type proc (rw,nosuid,nodev,noexec,relatime)
udev on /dev type devtmpfs (rw,nosuid,relatime,size=3990276k,nr_inodes=997569,mode=755)
devpts on /dev/pts type devpts (rw,nosuid,noexec,relatime,gid=5,mode=620,ptmxmode=000)
tmpfs on /run type tmpfs (rw,nosuid,noexec,relatime,size=802840k,mode=755)
/dev/sda8 on / type ext4 (rw,relatime,errors=remount-ro)
securityfs on /sys/kernel/security type securityfs (rw,nosuid,nodev,noexec,relatime)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /run/lock type tmpfs (rw,nosuid,nodev,noexec,relatime,size=5120k)
tmpfs on /sys/fs/cgroup type tmpfs (ro,nosuid,nodev,noexec,mode=755)
cgroup on /sys/fs/cgroup/unified type cgroup2 (rw,nosuid,nodev,noexec,relatime,nsdelegate)
cgroup on /sys/fs/cgroup/systemd type cgroup (rw,nosuid,nodev,noexec,relatime,xattr,name=systemd)
pstore on /sys/fs/pstore type pstore (rw,nosuid,nodev,noexec,relatime)
cgroup on /sys/fs/cgroup/pids type cgroup (rw,nosuid,nodev,noexec,relatime,pids)
cgroup on /sys/fs/cgroup/net_cls,net_prio type cgroup (rw,nosuid,nodev,noexec,relatime,net_cls,net_prio)
cgroup on /sys/fs/cgroup/cpu,cpuacct type cgroup (rw,nosuid,nodev,noexec,relatime,cpu,cpuacct)
cgroup on /sys/fs/cgroup/hugetlb type cgroup (rw,nosuid,nodev,noexec,relatime,hugetlb)
cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,nosuid,nodev,noexec,relatime,cpuset)
cgroup on /sys/fs/cgroup/devices type cgroup (rw,nosuid,nodev,noexec,relatime,devices)
cgroup on /sys/fs/cgroup/rdma type cgroup (rw,nosuid,nodev,noexec,relatime,rdma)
cgroup on /sys/fs/cgroup/perf_event type cgroup (rw,nosuid,nodev,noexec,relatime,perf_event)
cgroup on /sys/fs/cgroup/blkio type cgroup (rw,nosuid,nodev,noexec,relatime,blkio)
cgroup on /sys/fs/cgroup/freezer type cgroup (rw,nosuid,nodev,noexec,relatime,freezer)
cgroup on /sys/fs/cgroup/memory type cgroup (rw,nosuid,nodev,noexec,relatime,memory)
systemd-1 on /proc/sys/fs/binfmt_misc type autofs (rw,relatime,fd=36,pgrp=1,timeout=0,minproto=5,maxproto=5,direct,pipe_ino=14856)
mqueue on /dev/mqueue type mqueue (rw,relatime)
debugfs on /sys/kernel/debug type debugfs (rw,relatime)
hugetlbfs on /dev/hugepages type hugetlbfs (rw,relatime,pagesize=2M)
fusectl on /sys/fs/fuse/connections type fusectl (rw,relatime)
configfs on /sys/kernel/config type configfs (rw,relatime)
tmpfs on /run/user/1000 type tmpfs (rw,nosuid,nodev,relatime,size=802836k,mode=700,uid=1000,gid=1000)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,relatime,user_id=1000,group_id=1000)
tmpfs on /run/user/1001 type tmpfs (rw,nosuid,nodev,relatime,size=802836k,mode=700,uid=1001,gid=1001)
gvfsd-fuse on /run/user/1001/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,relatime,user_id=1001,group_id=1001)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,relatime)
lou@lou-Latitude-E6420:~$ 

Disk /dev/sda: 298.1 GiB, 320072933376 bytes, 625142448 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x5a3d9251

Device     Boot   Start       End   Sectors   Size Id Type
/dev/sda1  *       2048   1050623   1048576   512M  b W95 FAT32
/dev/sda2       1050624   2101247   1050624   513M  b W95 FAT32
/dev/sda3       2101248   3151871   1050624   513M  b W95 FAT32
/dev/sda4       3153918 625141759 621987842 296.6G  5 Extended
/dev/sda5       3153920   4202495   1048576   512M  b W95 FAT32
/dev/sda6       4204544   5253119   1048576   512M  b W95 FAT32
/dev/sda7       5255168   6303743   1048576   512M  b W95 FAT32
/dev/sda8       6305792 625141759 618835968 295.1G 83 Linux

the devs above are shown as icons on the desktop.  They are mountable (thow empty)

---

### Post by TheFu on 2020-09-30
Last time I looked, **gio** and **gvfs** mounts didn't actually show up in the /etc/mtab, which is what the **mount** command (no options) displays.  Gio/gvfs are Gnome inventions.

```
gio mount --list
``` is how the Gnome gio subsystem learns which things it can mount.  GUIs based on Gnome, like Xfce, will show those pseudo-mounts.
[https://developer.gnome.org/gio/stable/gio.html](https://developer.gnome.org/gio/stable/gio.html) and other gnome.org pages have details.

For others - looks like the OP didn't just copy/paste, too bad:
```
Disk /dev/sda: 298.1 GiB, 320072933376 bytes, 625142448 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x5a3d9251

Device Boot Start End Sectors Size Id Type
/dev/sda1 * 2048 1050623 1048576 512M b W95 FAT32
/dev/sda2 1050624 2101247 1050624 513M b W95 FAT32
/dev/sda3 2101248 3151871 1050624 513M b W95 FAT32
/dev/sda4 3153918 625141759 621987842 296.6G 5 Extended
/dev/sda5 3153920 4202495 1048576 512M b W95 FAT32
/dev/sda6 4204544 5253119 1048576 512M b W95 FAT32
/dev/sda7 5255168 6303743 1048576 512M b W95 FAT32
/dev/sda8 6305792 625141759 618835968 295.1G 83 Linux
```

What's the deal with all those FAT32 partitions?  I would expect 1 FAT32 and 1 Linux, nothing more.

---

### Post by scorp123 on 2020-09-30
> **TheFu said:**
>  ```
Disk /dev/sda: 298.1 GiB, 320072933376 bytes, 625142448 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x5a3d9251

Device Boot Start End Sectors Size Id Type
/dev/sda1 * 2048 1050623 1048576 512M b W95 FAT32
/dev/sda2 1050624 2101247 1050624 513M b W95 FAT32
/dev/sda3 2101248 3151871 1050624 513M b W95 FAT32
/dev/sda4 3153918 625141759 621987842 296.6G 5 Extended
/dev/sda5 3153920 4202495 1048576 512M b W95 FAT32
/dev/sda6 4204544 5253119 1048576 512M b W95 FAT32
/dev/sda7 5255168 6303743 1048576 512M b W95 FAT32
/dev/sda8 6305792 625141759 618835968 295.1G 83 Linux
```

What's the deal with all those FAT32 partitions?  I would expect 1 FAT32 and 1 Linux, nothing more.

Yeah exactly!?? ... why would you have 6 x Windows partitions, 512 MB each??

---

### Post by lou6 on 2020-09-30
I assume you're not asking me :)  I wouldn't know how to create them... did you see the screenshot in post 19?  No-one knows where they came from yet there they are...

---

### Post by CelticWarrior on 2020-09-30
They're probably "EFI" partitions. Now the question is why? Did the installer created each one per installation (the number match the reported attempts) because of MBR? Or were they manually created because reasons?

Here's my suggestion: Run a live session and *before* installing again, open Gparted, select the target drive and then Device > New partition table making sure you select GPT. Then install as normally. If my suspicions are correct the problem will be gone (but one more bug to the list).

---

### Post by lou6 on 2020-09-30
CelticWarrior;  isn't there another way to fix this - I've reinstalled my system 7 times in 3 days at <> 2 hours per install.  Only so many tries before I really screw up the file restoring (the important part).

Seriously, you lost me at "run a live session" - if you can tell me what to do step-by-step I'd really appreciate it.  My only experience with Gparted is formatting some usb drives.

Thanks

---

### Post by scorp123 on 2020-09-30
> **lou6 said:**
> I've reinstalled my system 7 times in 3 days at <> 2 hours per install.

So you're experienced with installing? Please reinstall and nuke those partitions. 7 times or 8 times... see it as learning experience.

And sometime in the far future, you may want to familiarize yourself with **Ansible**. That way all your installations always turn out the same way, every time. Reinstall 8 x imes, or 8000 x times, doesn't matter. Your installations will be fully automatic, 100% identical and perfect, each time. But that's for another thread.

---

### Post by TheFu on 2020-09-30
> **lou6 said:**
> CelticWarrior;  isn't there another way to fix this - I've reinstalled my system 7 times in 3 days at <> 2 hours per install.  Only so many tries before I really screw up the file restoring (the important part).

I see said the blind man!  Click!  Bing!
I wouldn't reinstall.  I'd figure out which 1 (there's only 1) was being used and use fdisk or gparted to delete the others.

Let me look back through to see if I can figure out which can be deleted.

Ok, you want to keep this one:
```
UUID=6CB1-5EBF /boot/efi vfat 
```
All the others can be deleted. If you run 
```
blkid |grep 6CB1-5EBF
```
Then the output for that should have 1 line with the first field showing the /dev/sda**[COLOR="#FF0000"]?[/COLOR]** you need to leave alone. Just figure out if that is sda1 or sda2 or sda.... whatever.  There are other ways to determine the partition besides using **blkid**.

How those got created are unknown to me.  My EFI system has just 1.  For my system, it looks like this:
```
$ blkid |grep vfat
/dev/sda1: UUID="E7E6-D023" TYPE="vfat" PARTLABEL="EFI System Partition" PARTUUID="8cd37b7a-fdc2-4f65-ac40-e8936f30012b"

```
gparted is the easier tool to use. Be certain that sda is selected, then right click on each of the small vfat/FAT32 partitions that are NOT UUID=6CB1-5EBF and delete them. Don't delete the Extended partition (/dev/sda4) or the Linux partition (/dev/sda8) or 6CB1-5EBF.  When this is done, there will be some free space inside and outside the Extended Partition. I wouldn't worry too much, but if you like, it can be cleaned up with some effort. I think I'd wait until there was some other reason before bothering. ;)

Apply the changes and close gparted down. I don't think anything else should be needed, but if you like, you can run **sudo update-grub**.

---

### Post by TheFu on 2020-09-30
Ansible makes no sense for an end-user who isn't working as an admin in IT.  Let's keep this easy for today.  I wouldn't use ansible if there weren't at least 5 systems that needed to be configured.

Scripting package installs is 10x easier that dealing with ansible.  I like ansible and use it, btw. It just brings hassles that aren't needed for a 1-2 system LAN.

If the time is being spent on installing packages, that can be scripted to take 5 minutes with only 10 seconds of your time. Same for many custom settings. Moving systems/reinstalling systems shouldn't take over 30 min wall-clock time with only about 15 minutes of human "pay attention" time needed.  Tools like ansible have a learning crve and every 12-24 months, those playbooks will deprecate, so they need to be reworked. otoh, a few 5 line scripts work for decades.

This s why am not a fan of ansible for a typical home end-user. IT Pros, t is a good skill to have, definitely.

---

### Post by scorp123 on 2020-09-30
> **TheFu said:**
> Ansible makes no sense for an end-user who isn't working as an admin in IT. I disagree on that one. Especially if you for some reasons install and reinstall your Linux OS a lot it can save you lots of time, e.g. automagically getting your packages and config files back instead of having to manually click your way through whichever package manager.

> **TheFu said:**
>  Let's keep this easy for today.  
I already said that. This is off-topic and shouldn't be discussed here.

> **TheFu said:**
>  I wouldn't use ansible if there weren't at least 5 systems that needed to be configured. I've also met people who wouldn't use it even though they are responsible for 500 systems. I find it's worth knowing even if you only have 1 x system and for whatever reasons you end up having to install / reinstall it more often than you would like to. But to each their own.

---

### Post by The Cog on 2020-09-30
The "mount points" on your desktop are icons that you can click in order to mount those unexplained FAT partitions on the hard disk.
There are 3 ways to get rid of them:

1: Use Settings ->  Desktop -> Icons and un-check removable devices / disks and drives. However, this means you don't get an icon for real removable drives when you plug them in.

2: Make fstab entries for them and mark them as noauto, meaning don't automatically mount them. Here is a line you can add to /etc/fstab to stop /dev/sda1 from making an icon on your desktop. Just add a similar line for each unused partition:
```
/dev/sda1  /mnt/sda1   auto  defaults,noauto  0  0
```

3: Delete the unused partitions with gparted or similar. You can't do that while they are mounted of course.

P.S. Ansible is well worth looking at. I always fresh install rather than upgrade, and ansible puts all my customisations back quickly and reliably - saves me hours.

---

### Post by lou6 on 2020-10-01
Thank you to everyone who posted here and helped.  One final question - is it possible to run Gparted and reformat the ext4 partition prior to installing Xubuntu 20.04.  In other words, can I reformat the partition currently in use?

---

### Post by TheFu on 2020-10-01
> **lou6 said:**
> Thank you to everyone who posted here and helped.  One final question - is it possible to run Gparted and reformat the ext4 partition prior to installing Xubuntu 20.04.  In other words, can I reformat the partition currently in use?

Only if you want massive data loss. The system will complain, but as root, you can shoot yourself in the head, if you like. The trick is to have enough OS remaining during the wipe that the tools to do the wipe are available.  I wouldn't bother doing this.

This seems unnecessary to me.

I would .... 

If you want to wipe a disk, then wipe the disk.  Boot from any Ubuntu Desktop Installer, choose "try ubuntu" (xubuntu/lubuntu/ubuntu/ubuntu-mate .... doesn't matter), then use a disk wiping tool. There must be 50 of those. I'd use **dd** or **ddrescue**, but you can use whatever you like. If you just wipe the first 2K-2M of a disk, then create a new partition table (GPT, hopefully), that would be equivalent.  dd can do the wipe of 2K-2M from the beginning. fdisk or gparted or parted or partman can be used to create a GPT.  The only GUI program I trust with partitioning is gparted.  I've been screwed by all the others.

If you want random data used during the wipe, use /dev/urandom as the "input file".
If you want zeros used during the wipe, use /dev/zero as the "input file".

I would use zeros if I planned to reload the OS. For for 2M, it really doesn't matter.

---

### Post by lou6 on 2020-10-01
I'm thinking that when I reinstall Xubuntu 18.04 on this machine I definitely don't want to see those mount points again.  I have Gparted Live CD - can I use that to reformat the ext4 partition?

---

### Post by lou6 on 2020-10-01
I'm thinking that when I reinstall Xubuntu 18.04 on this machine I definitely don't want to see those mount points again.  I have Gparted Live CD - can I use that to reformat the ext4 partition?  I hate being such a noob...

Sorry, meant to edit the last post...

---

### Post by The Cog on 2020-10-01
Yes you can use a live gparted to format the partition, or delete the partition, or create a new empty partition table. 
I it was me, I would delete all the existing partitons, and start with that blank disk.
But the Ubuntu installer has a "try Ubuntu" mode which has gparted on it anyway. So for anyone else reading this, you don't need to get a separate gparted live CD.

---

### Post by lou6 on 2020-10-01
Thank you.  I never knew that "try ubuntu" had that function.  If you read through this whole thread you know that Xubuntu 20.04 LTS malfunctioned on me early on and subsequent re-installs resulted in adding sda2, sda3, and so on all the way to sda7, all of which were cluttering my desktop and (I believe) causing more weird behavior.  This has taken a bit of the trust out of me and I'm a bit hesitant to try 20.04 again anytime soon.  I had another laptop with 18.04 installed that was serving as an entertainment center so this morning I added my wife as a second user, restored all the files from backups of now-disabled computer and made that our main machine.  At some point I plan to get back to the failed computer and set it up properly which is why I'm interested in learning how to clean up and fix the SDA mayhem. I have liveGparted on a floppy and now that I know that "try ubuntu" has the same function I will probably use that.  Thanks for responding.  I'll mark this thread as solved.

---

### Post by CelticWarrior on 2020-10-01
GParted is software, not a "function" and yes, it's included in the live session along with many others. A live session is a full Ubuntu running from the installation media (and RAM).

> [COLOR=#000000]all of which were cluttering my desktop and (I believe) causing more weird behavior[/COLOR]
No, they were completely harmless.

> [COLOR=#000000]I'm interested in learning how to clean up and fix the SDA mayhem[/COLOR]
Not so long ago I gave you a [suggestion]("https://ubuntuforums.org/showthread.php?t=2451148&p=13989654#post13989654") exactly for that. But then you din't like it and other suggestions came.

---

### Post by The Cog on 2020-10-02
The "Try Xubuntu" option needs a bit more RAM than the straightforward install, but I prefer to do an install from the live OS because:
* I can connect to the wifi and can fetch some updates while it is installing
* It uses the wifi connection to figure out and suggest the location/language to configure
* It configures the wifi password into the installed OS for you
* I can browse the internet while the installer chugs away in the background

---

