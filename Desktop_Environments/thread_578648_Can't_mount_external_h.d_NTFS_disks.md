---
title: "Can't mount external h.d NTFS disks"
date: 2007-10-17
forum: Desktop Environments
---

### Post by CoolRat33 on 2007-10-17
Hi
I just switched to Kubuntu from Gnome Mint and found that I can't access my NTFS external disks.  I installed NTFS-3g using Adept packages and turned on "Write" for external devices.
But the drives still do not appear either on the Desktop or in /Media

When I examine the System Settings -- Advanced tab -- Disk and File Settings, it reports that the 3 drives exist as /dev/sdb1, /dev/sdb2, and /dev/sdb3
But there was no mount point specified.
I specified "/media" with "Type" set as "Auto", and Enabled each drive.  But I"m not able to access the data.  I chose "One User at a Time may Enable/Disable".

What am I doing wrong?  Why can't I access these drives?
And why didn't Ubuntu recognize the drives immediately as in MINT?

Please give me some advice and some straightforward instructions- I'm still pretty new to this. Please forgive my dunciness:)

---

### Post by taurus on 2007-10-17
Open a terminal and see if you can mount it by hand.

```
sudo mkdir /media/sdb1
sudo mount -t ntfs-3g /dev/sdb1 /media/sdb1
ls -la /media/sdb1
```

---

### Post by CoolRat33 on 2007-10-17
Thanks!
I opened Terminal and pasted in the code but I got this message:
"mkdir: cannot create directory `/media/sdb1': Read-only file system"

When I examine the /media directory in Konqueror, it has a LOCK icon and I can't access it. 
How and why is it locked?:confused:

Looking forward to getting my Kubuntu system up and running.

---

### Post by jaygo on 2007-10-18
First, are you sure sdb is your external drive? If so, it has three partitions. Are they all NTFS partitions?

Assuming the above is true, we'll first unmount the drive & start from scratch.
```
sudo umount /dev/sdb1 /dev/sdb2 /dev/sdb3
```
that should do it. Then, under Disk & Filesystems, choose a partition you want to mount and try changing the Type from auto to NTFS. I'm hoping that this uses the ntfs-3g instead of the old ntfs, otherwise you'll probably have to do this all through the console. You can play around with the options & label later. For now, set  the mount point to a folder in /media ... say, /media/ntfsdrive (it will create it for you). I don't think you want to set it to a folder with files in it -- that would mean something is probably already mounted there -- so make up a new folder or check for any files in /media/ntfsdrive. Set Mount Permission to "Any user ...". Hit OK, then enable the partition. Let's see what happens ...

[SIZE="4"]_background info_[/SIZE]

The whole issue is a bit tricky at the moment, though I believe it's going to get a lot easier tomorrow (with the release of 7.10). There are a few things that play into this problem:
[LIST=1]
[*]NTFS filesystems aren't/weren't easy to work with. NTFS-3g takes care of this and makes them play nice. Mint 3.x implements ntfs-3g automagically while ubuntu 7.04 doesn't, so that's probably why you're suddenly having issues.
[*]I'm not sure what the lock icon is ... but I'll guess it means 'read-only'. You can check from console by going to the containing directory (/media/ for example) and typing "ls -l" in the console. If you understand all the rwx stuff then it will make sense.
[*]fstab. Do you have any entries for this NTFS drive saved in your fstab file? Those can automate mounting but can also get in the way if they're not done correctly. Also, when you manually create an entry for an NTFS volume in /etc/fstab it needs to be given a filetype of ntfs-3g for it to work (well). This is according to my best recollection ... That filesystem type will give it automatic read/write mounting.
[/LIST]

By the way, welcome to kubuntu. I went through the exact same migratory pattern last month. First time Windows to Linux full migration (no dual booting :) and went through a few PC hardware changes too:
[COLOR="RoyalBlue"]XP[/COLOR] > [COLOR="PaleGreen"]Linux Mint 3[/COLOR] (gnome) > added [COLOR="Blue"]kde[/COLOR] > [COLOR="Blue"]kubuntu[/COLOR] on new PC (mint doesn't allow RAID 0 installs) > [COLOR="Sienna"]ubuntu server[/COLOR] on old PC > fresh [COLOR="Blue"]kubuntu[/COLOR] install on new PC

---

### Post by CoolRat33 on 2007-10-18
Hi 
Thanks for your reply.  

My external h.d. a 300gb drive partitioned into 3 parts.

I ran the unmount command, then changed the settings in Disk & Filesystems as you recommended.  
But when I tried to 'ENABLE' it, I received this message

An error occurred while enabling /media/StorDisk1.
The system reported: mount: special device /dev/sdb1 does not exist

When I ran ls -l on /media, this is the report:

ray@RayComp:/media$ ls -l
total 30
lrwxrwxrwx 1 root root    6 2007-10-17 22:30 cdrom -> cdrom0
dr-xr-xr-x 1 root root 2048 2007-06-25 13:55 cdrom0
drwxr-xr-x 2 root root 4096 2007-10-17 22:30 cdrom1
drwxr-xr-x 2 root root 4096 2007-10-17 22:30 cdrom2
drwxrwxrwx 1 root root 8192 2007-10-17 14:29 sda1
drwxr-xr-x 2 root root 4096 2007-10-18 01:24 StorDisk1
drwxr-xr-x 2 root root 4096 2007-10-18 01:25 StorDisk2
drwxr-xr-x 2 root root 4096 2007-10-18 01:26 StorDisk3

Now what should I do?

Hmm.. we have both gone through the same migratory process. I also used Gnome, then added KDE but the result was quite messy and my notebook h.d. is much too small to handle both Gnome and KDE. I decided to go with  Kubuntu.

Can I upgrade my 7.04 to 7.10 and hopefully automatically fix this mess?  Mint really did a very good job of automating the entire process for newcomers.

---

### Post by jaygo on 2007-10-20
Interesting .. I hadn't seen KDE's disk management GUI until you pointed it out. So I played around with the other day trying to automount my backup drive by label, anyway, got the same error you did.

Let's try doing it manually:
[LIST=1]
[*]Edit /etc/fstab
[LIST]
[*]you'll have to do this as root so ...
[*](from the run command box) kdesu kate /etc/fstab (this opens the file as root in your favorite graphical text editor)
[*]save a backup of the file somewhere
[*]add a line for each partition of your ntfs drive
[LIST=1]
[*]/dev/sdb1   /media/ntfs1  ntfs-3g  exec,rw,user,locale=en_US.utf8    0 0
[*]/dev/sdb2   /media/ntfs2  ntfs-3g  exec,rw,user,locale=en_US.utf8    0 0
[*]/dev/sdb3   /media/ntfs3  ntfs-3g  exec,rw,user,locale=en_US.utf8    0 0
[/LIST]
[*]remove any existing lines that reference your ntfs drive by UUID for now
[LIST]
[*]if you're not sure about this, you'll have to search for how to find the UUID of a specific drive ... I forget the command(s).
[/LIST]
[*]save the file
[/LIST]
[*]reload fstab
[LIST]
[*]sudo mount -a         (mounts everything listed in fstab)
[/LIST]
[*]look for your partitions in /media/whatever
[/LIST]

At this point, your three NTFS partitions should automatically mount every time you reboot. This will be based on the fact that your drive is /dev/sdb. If that changes -- say if you add a USB key while your NTFS drive is unplugged -- then this manual config won't fit the picture any more. However, I think this will get the job done and let you do any future tweaking from the nice & friendly Disk & Filesystem manager. Also, I'm learning the advantage to giving every partition a unique label so you don't have to deal with /dev/sdfasdfafa or UUIDs. The label stays on the drive too.

GLHF

I have no idea if 7.10 will do a better job of this. Regardless, it would be a good idea to upgrade. In fact, if you find it takes care of NTFS better, please let me know (I don't have any ntfs drives atm). Hopefully whatever ubuntu did to add ntfs-3g support will end up in Kubuntu without any effort.

I'm with you on Mint. It's very nice and I'll probably put some friends & family on it soon.

---

