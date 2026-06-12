---
title: "Automounting and changing the mount point."
date: 2009-04-01
forum: General Help
---

### Post by tourist on 2009-04-01
I'm trying to automount my NTFS partition so that I could automatically access my Windows files and my Firefox profile.
So I tried doing that through the NTFS configuration tool, but in newbie fashion, I wrote "startup" and accidentally configured that as my mount point for that partition. How do I get it changed back to /media/disk?

Also, I am now getting a message saying that I am not privileged to mount the volume when trying to do so from the Disk Mounter. I can still mount it from the terminal, but that's not exactly ideal.

Thanks for your help.

---

### Post by skierkyles on 2009-04-01
Fstab!

[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
^This is a pretty good thread to read up on it.

But pretty much you would do

```
sudo fdisk -l
```
Which will then display all your drives and partitions.

```
sudo gedit /etc/fstab
```
This is where you configure what drives you want to mount at boot, they can be anything from NTFS to SMB shares, and you can mount them wherever you want.
So what you would want for auto mounting a ntfs drive would be something like this..

```
/dev/sd(what ever hard drive you are trying to mount)  /MountPoint/   ntfs    defaults    0     0
```
But you need to have the create the directory before you can mount there.

Then you can figure out if it worked by doing.
```
sudo mount -a
```

________________________
Here's the customized bit of mine to give you some help.
```

#Me HardDrives YARR!
/dev/sda2	/home/kyle/Drives/Music	ntfs	defaults   0	0
/dev/sdb1	/home/kyle/Drives/Movies	ntfs	defaults	0	0
#Me Network Mount Points YARR!!
//192.920.9.012/Share	/home/kyle/Share	smbfs	defaults	0	0
//192.920.9.012/Mesh	/home/kyle/Mesh	smbfs defaults	  0	  0

```

---

### Post by coffeecat on 2009-04-01
> **skierkyles said:**
> ```
/dev/sd(what ever hard drive you are trying to mount)  /MountPoint/   ntfs    defaults    0     0
```

If the OP uses the ntfs driver they'll only get read access. For full read-write access they need the ntfs-3g driver. So that line would need to be something like:

```
/dev/sd_whatever    /media/mountpoint    ntfs-3g    defaults    0 0
```**tourist**, you can create/use /media/disk if you want, but /media/disk is the all-purpose mountpoint that the system uses when automounting drives. If you use /media/disk, and it automounts a second drive, it will be something like /media/disk-1. Which is not a problem, but you might want something more descriptive like /media/ntfs_partition. Anyway, create a permanent /media/disk with:

```
sudo mkdir /media/disk
```and substitute /media/disk for my /media/mountpoint and skierkyles' /MountPoint/.

---

### Post by skierkyles on 2009-04-01
> **coffeecat said:**
> If the OP uses the ntfs driver they'll only get read access. For full read-write access they need the ntfs-3g driver.

What is the difference between the ntfs and ntfs-3g driver? beacuse I have read and write with just the ntfs driver.

---

### Post by nebileix on 2009-04-01
Try using the gnome-mount command if u are using gnome.

---

### Post by coffeecat on 2009-04-01
> **skierkyles said:**
> What is the difference between the ntfs and ntfs-3g driver? beacuse I have read and write with just the ntfs driver.

My apologies. You are right and I am out of date. :oops:

The ntfs driver is a kernel driver , but until the release of a fairly recent version of the kernel, the ntfs driver was read-only, or at least unreliable in write mode. I now discover that the ntfs-3g driver is an obsolete fork of ntfsmount, although it's working well enough in my fstab.

I need to do some more digging around. Sorry about that. :(

---

### Post by skierkyles on 2009-04-01
> **coffeecat said:**
> My apologies. You are right and I am out of date. :oops:

The ntfs driver is a kernel driver , but until the release of a fairly recent version of the kernel, the ntfs driver was read-only, or at least unreliable in write mode. I now discover that the ntfs-3g driver is an obsolete fork of ntfsmount, although it's working well enough in my fstab.

I need to do some more digging around. Sorry about that. :(

Ah no prob, I was just making sure I wasnt messing up my hard drives lol. :p

---

### Post by coffeecat on 2009-04-01
All very interesting. If I use 'ntfs' in my /etc/fstab, it works just as well as 'ntfs-3g', but whether I use 'ntfs' or 'ntfs-3g' in fstab, /etc/mtab is showing 'fuseblk' for the driver.

I give up. :cry:

:wink:

---

### Post by tourist on 2009-04-01
Very interesting, and I'm making progress, so thank you.

A few things I still can't quite make work:

1. I basically got the NTFS partition to automount on startup by editing the fstab and adding 'sudo mount -a' to the Startup Programs in the Session Preferences. However, I still get an error saying I am not privileged to unmount the volume when trying to do so from the Disk Mounter. Not a major problem since I don't really see a reason why I would ever want to unmount the partition, but I would still like to get a clarification if possible.

2. After managing to get my local NTFS to automount, I tried adding a network partition on fstab as well. Entering 'sudo mount -a' at the terminal gets me a "Failed to access volume 'smb://mediacenter/d/': No such file or directory", which, naturally, leads me to assume 'smb://mediacenter/d/' is not the correct value to substitute '/dev/sda1' for a network location. But what is?

3. Since I'm still Dual-booting, I would also like to have aMule get its temporary files from the NTFS partition, so that my downloads would continue on both systems.I also want to have aMule start on startup, but when it does that, the NTFS partition isn't mounted yet and aMule reverts back to its original temp folder. Is there a way to maybe, I don't know, delay aMule for a bit, or to instruct some sort of order for the startup applications?

Sorry if it's a bit much. I appreciate it.

---

### Post by skierkyles on 2009-04-01
> **tourist said:**
> 

2. After managing to get my local NTFS to automount, I tried adding a network partition on fstab as well. Entering 'sudo mount -a' at the terminal gets me a "Failed to access volume 'smb://mediacenter/d/': No such file or directory", which, naturally, leads me to assume 'smb://mediacenter/d/' is not the correct value to substitute '/dev/sda1' for a network location. But what is?



You need to use the actual IP address of the computer. Like this

```
//192.431.0.963/Share	/Where/You/Want/It/Mounted	smbfs	defaults	0	0
```

Also make sure you have smbfs instead of ntfs.

you may need to install smbfs.

---

### Post by coffeecat on 2009-04-01
> **tourist said:**
> 1. I basically got the NTFS partition to automount on startup by editing the fstab and adding 'sudo mount -a' to the Startup Programs in the Session Preferences. However, I still get an error saying I am not privileged to unmount the volume when trying to do so from the Disk Mounter. Not a major problem since I don't really see a reason why I would ever want to unmount the partition, but I would still like to get a clarification if possible.

You don't actually need 'sudo mount -a' in the startup programs. Whatever is listed in fstab will be mounted during the bootup process. 'sudo mount -a' merely plods through fstab and mounts anything not mounted, so if you put it in startup programs, everything's already mounted anyway. The command is useful for when you're fiddling with fstab during a session and want to change things on the fly.

And the reason you can't use Disk Mounter to unmount partitions mounted on bootup is that they were mounted by root. You need root permissions. So, open a terminal and:

```
sudo umount /dev/whatever
```**or**

```
sudo umount /media/mountpoint
```That's umount, not unmount. And obviously, change mountpoint or whatever to - um - whatever. :wink:

---

### Post by drs305 on 2009-04-01
> **coffeecat said:**
> All very interesting. If I use 'ntfs' in my /etc/fstab, it works just as well as 'ntfs-3g', but whether I use 'ntfs' or 'ntfs-3g' in fstab, /etc/mtab is showing 'fuseblk' for the driver.

Yes, ntfs-3g is now just a link to ntfs. FUSEBLK (FUSE=Filesystem in Userspace) is just how ntfs partitions show up. It's a FUSE block device.

Speaking of outdated, smbfs is also now deprecated to "cifs" (common internet file system). If you mount with "smbfs" and check out the "mount" command, it's listed as "cifs".

So much to keep up with...  ;-)

---

### Post by kherio on 2009-04-03
Hi all,
And what happend if you don't have X and you want to mount it on the same mountpoint? 

I mean, when you plug the driver the system "attach" it on sda, sdb or sdc. What I whant to know is if it's poosible to mount always in the same mountpoint even if the system attach it on sdb and tomorrow on sdc.

Thx in advance
kherio

---

### Post by drs305 on 2009-04-03
Since this wasn't your thread I've sent you a Private Message providing your options.

---

