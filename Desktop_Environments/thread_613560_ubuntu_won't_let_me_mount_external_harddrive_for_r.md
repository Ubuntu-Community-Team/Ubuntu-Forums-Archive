---
title: "ubuntu won't let me mount external harddrive for read acess"
date: 2007-11-15
forum: Desktop Environments
---

### Post by mistamoni on 2007-11-15
A month ago I somehow got a virus (even with all the anti-virus software installed) on my western digital 400GB external HD, and it stopped working altogether.  This is definitely not the best news for most people, but even worse when you're a professional photographer with many important photographs.  Anyways, long story short... even though the HD is severly damaged and messed up, and makes a loud cranking noise when trying to access it, it opens up on ubuntu and allows me to read it.  

Here's my problem.  I bought another external HD and converted 150 gigs to FAT32, so it's showing up on ubuntu to allow me to transfer files.  However, all of the sudden my bad harddrive can't mount.  This is strange because I had opened it a few times already, and transferred some data to my ipod.  The following message comes up when trying to access it:

[INDENT]Can not mount volume.  Unable to mount the volume 'My Book'[/INDENT]

when I click more detail, it gives this:

[INDENT]Volume is scheduled for check.  Please boot into Windows TWICE, or use the 'force' mount option.  For example, type on the command line:     mount -t ntfs-3g/dev/sdc1/media/My Book -o force Or add the option to the relevant row in the /etc/fstab file:    /dev/sdc1/media/My Book ntfs-3g defaults, force 0 0[/INDENT]

Now I got ubuntu just recently (and it's so much better than windows by the way), so I don't know much about it.  I have read some other threads and tried to force mount it with the following command:

sudo mkdir /media/external
sudo mount /dev/sda1 /media/external -t ntfs-3g -o nls=utf8,umask=0222

but it didn't work.  The only thing that kinda worked a bit (tried to read the drive before giving the error message) was this: sudo mount -t ntfs-3g /dev/sdb1 /media/hd-ntfs -o force.

Please help, as I desperately need to get some of my more memorable photographs from my HD before I send it in for replacement.  If you can, please provide step by step guide as I'm new to the system.

---

### Post by tact on 2007-11-15
You are doing pretty well...  the command you used ...

```
sudo mount -t ntfs-3g /dev/sdb1 /media/hd-ntfs -o force
```

...is spot on.  (Assuming that is a ntfs formatted drive).  That should have seen the external drive mounted on the folder /media/hd-ntfs

You did make the directory first?
```
sudo mkdir /media/hd-ntfs
```

---

### Post by mistamoni on 2007-11-15
Yes, the external drive is NTFS, however, the code is not working.  The drive is showing up under places>computer just fine, and I can even right click on properties... but it's just not mounting or opening.  I've tried the following code:

```
sudo mount -t ntfs-3g /dev/sdb1 /media/hd-ntfs -o force
```

and it said "Failed to acess 'dev/sdb1/', no such file or directory.

I thought if I changed it to this it may work:

```
sudo mount -t ntfs-3g /dev/sdb1 /media/My Book -o force
```

But then I get this message in the terminal:

[INDENT]distagon@Distagon:~$ sudo mount -t ntfs-3g /dev/sdb1 /media/My Book -o force
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .
[/INDENT]

Any other suggestions?

---

### Post by cdinis on 2007-11-15
I have a similar problem.
I start my computer on Windows XP (I've dual boot) turn on my external harddrive and do a "safely remove hardware", turn off my external harddrive after that. Start with ubuntu and I can mount the external harddrive without problems.

Hope it helps.

---

### Post by mistamoni on 2007-11-15
Nevermind, I fixed it.  All I had to do was restart the computer and try again.  

```
sudo mount -t ntfs-3g /dev/sdb1 /media/hd-ntfs -o force
```

It said that it was a dirty drive, but I was able to force mount it.  Thanks for the help.

---

