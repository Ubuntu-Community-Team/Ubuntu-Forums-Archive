---
title: "Unity: what's that icon? and why? (Ubuntu 12.10)"
date: 2013-01-31
forum: Desktop Environments
---

### Post by ArlieS on 2013-01-31
Absolute dumb newbie query here, with a twist: 

- In my 12.10 installation, running unity, in the lefthand icon bar (=? "launcher") I see 2 icons which look like they are intended to represent disk drives. One has the tooltip "315 MB Volume" and the other has the tooltip "OSDisk". 
- This is a dual boot system, with an NTFS partition (windows 7), an ext4 partition (ubuntu 12.10), and some kind of relatively tiny thing I suspect of being some kind of boot partition
- mount and df report a lot of filesystems, most virtual, but none appear to be 512 MB
- I now have a bunch of NFS file systems mounted, some from /etc/fstab (ie at boot) but these two icons are the only "disks" represented and they've been there since I first installed the system, before I figured out which package to install to make mount work with nfs file systems

I presume the "OSDisk" would be /dev/sda5, mounted at /   

But what is the "512 MB disk", and why do I have an icon for a file system that isn't even mounted? Is clicking the icon going to cause some kind of automount behaviour? Is it something insane like the swap partition, which really should NOT be that tiny  AFAIK. 

I have NOT seen a similar icon on 12.04, installed as the only OS, nor on 12.04.01, installed with wubi on top of windows 7.

The "twist" is that I'm wondering about the value - or otherwise - of putting such a puzzle in the launcher.  How is a true Unix newbie [someone who doesn't know /etc/fstab from Adam] going to figure out what this is, or have a use for it?


Finally, I clicked on the OSdisk icon, and got a windows-like graphical file browser - and an extra mount  
          /dev/sda2 on /media/arlie/OSDisk type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)

Judging by the contents, it's the NTFS5 file system associated with the windows 7 installation on this system. 

Frankly, I defy any naive user to figure this out; windows goes out of its way to discourage people from looking at what's directly in what they see as C:\ or D:\

Also, judging by my recent experience - which led to a complete reinstall of both windows and linux - and people's comments on my descriptions of that experience - it's _still_ unsafe to write to NTFS from linux - so why isn't this mount at least read-only? Is it safe to have such a tempting icon turn up automatically? And this goes doubly for the other icon, since this does seem to be a partition involved in booting - ie "mess up at your own risk". 

I think there's a usability bug somewhere in here, but I can't figure out how to express it. Otherwise I'd probably be writing this to the Ubuntu bug tracking system.

---Update--

I closed the window, and the mount didn't go away. 
I then tried to umount one of these file systems, and got:
$ umount /media/arlie/OSDisk
umount: /media/arlie/OSDisk is not in the fstab (and you are not root)

When I did sudo umount /media/arlie/OSDisk the mount went away - no error message about fstab.

So, I mounted it without privilege, but apparently need privilege to get rid of it?

---

### Post by mc4man on 2013-01-31
By default in 12.10 all other internal partitions (devices) will be shown in the unity launcher. This doesn't necessarily mean they are mounted at login, just shown.
(clicking on the icon or clicking on the device (partition) in nautilus will then mount it if not automounted in fstab 

12.10 only has 2 options available, always show that device icon or never show that device icon (blacklist), even if actually mounted
To blacklist you right click on the icon > remove ..

The option & previous default of 'only show when mounted' was lost & never returned (really poor job there.

current bug on I've had for some time
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1053704](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1053704)

---

