---
title: "Best way to backup ubuntu?"
date: 2006-09-24
forum: Desktop Environments
---

### Post by dannythomas13 on 2006-09-24
hi guys, as everyone has i am sure, i have installed a lot of appz, i.e. netbeans with latest java and have customised a lot of settings, not just the panels and backgrounds etc etc. what is the best way to backup everything i have on ubuntu, i am a beginner and so far i have just been backing up my data, is there an app with a gui that can backup everything? or at least one that restores well?
thanks everyone
Danny =)

---

### Post by otis on 2006-09-24
I'd like to find information about this as well.  I am new to unbuntu and have spent a lot of time getting my system just the way I want it.  I have been looking around for a how-to or some documentation on this.

What apps are around to do backups with?

What all do I backup besides my home directory?  Config files, etc?

Thanks, Otis

---

### Post by gumbald on 2006-09-24
Your system can be backed up using just a few commands...
[http://www.ubuntuforums.org/showthread.php?t=81311](http://www.ubuntuforums.org/showthread.php?t=81311)

I started using this method a couple of weeks ago, and have taken a backup everytime I've changed something major. Can't vouch for the restore element of it yet, I've not messed my system up... yet.

---

### Post by tagra123 on 2006-09-24
For monthly backups I use partimage. 

I have a partition setup just for backups, but if you understand networking you can easily mount a network drive and backup to it.

I use the SystemRescueCD (GOOGLE FOR IT) but you can use ubuntu live cd too

by installing partimage on the live CD

apt-get install partimage.

and then mounting a backup partition

sudo mkdir /mnt/backups
sudo mount /dev/hdc4 /mnt/backups  

On your computer the "/dev/hdc4" may be different


and then running partimage

select the partition to backup and then select the file to backup to: /mnt/backups/backupofrootpartition092406-1016am

And proceed  through the remaining screens.

Creates a very reliable backup.

Just remember to mount the place you are backing up to. The partition you are backing up from cannot be mounted.

The only real drawback is you have to use the systemrescuecd or the live cd, but the advantage is that you have an exact image of the partition. Partimage also only backs up the portion of the partition containing data and saves space.

When finished the images can be burned to a cd.

The restores are reliable and don't require a lot of extra work to get your system running again.



For automatic hourly,daily, and weekly  backups of the home directory take a look at my scripts.

[http://www.ubuntuforums.org/showthread.php?p=1402091](http://www.ubuntuforums.org/showthread.php?p=1402091)
The script is great for things like the home folder, or other important files.

To restore from these backups simply copy the file(s) back to the original location.

---

### Post by crudolphy on 2006-10-10
Check out the following link for a how-to on backing up with Rsync

[http://www.howtoforge.com/rsync_incremental_snapshot_backups](http://www.howtoforge.com/rsync_incremental_snapshot_backups)

I followed this then modified the script to backup 4 machines (3 Ubuntu machines and 1 WinXP) on the same network and it is working flawlessly.  As others have stated I haven't had the opportunity to try a restore because I haven't had a crash.

I would also recommend reading the Linux Filesystem Hierarchy Version 0.65 by Binh Nguyen.  Which can be found here:

[http://www.tldp.org/guides.html](http://www.tldp.org/guides.html)

This will explain the linux filesystem and it's contents.  Other than for a bare metal restore you don't need to backup everything.  

Currently I backup:

/etc (all)
/root (all)
/usr (not all just some)
/var (all)
/home (all)

If your interested in doing a disk image (similiar to Ghost in the Windows world) have a look at:

[http://www.howtoforge.com/dedicated_server_backup_restore_systemimager](http://www.howtoforge.com/dedicated_server_backup_restore_systemimager)

This is next for me.  I will use the Rsync method above for snapshots on an hourly, daily, and weekly basis, then I think I am going to do an image on a monthly basis.  With the image I could do a bare metal restore from the last image and then restore the latest snapshot to put me within 6 hours (hourly's done on a 6 hour increment) of the crash.

The website [http://www.howtoforge.com](http://www.howtoforge.com) is a great website with a great forum where there is lots of help.

You may also want to check out the rsync web site at:

[http://rsync.samba.org/](http://rsync.samba.org/)

and the Systemimage website at:

[http://www.systemimager.org/](http://www.systemimager.org/)

All helpful places for me.

Chuck

---

### Post by domino on 2006-10-10
I don't know if this will help you the way you want to back up your current config.

I got used to using Automatix on every new install and install the script (sbackup) that backs up and restore files.

---

