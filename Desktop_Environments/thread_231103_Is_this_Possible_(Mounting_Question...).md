---
title: "Is this Possible? (Mounting Question...)"
date: 2006-08-06
forum: Desktop Environments
---

### Post by kd5kij on 2006-08-06
I'm rather new to Linux. I've only used Ubuntu for about a month. I've liked it so well that I'm trying to figure out how to get more disk space for linux. I've got an 80GB master, and a 10GB slave. I currently have the entire Ubuntu system (8.2GB root, 80MB boot, and 1GB swap) on the 10GB drive. 

I'm planning on repartitioning my 80GB drive with a 25GB NTFS partition for Windows, and use the rest of the drive for linux. I'm thinking about putting my /home, /usr, and /opt directories there as well as a sizeable FAT32 partition for file swapping. 

My question is if this can be done with reinstalling Ubuntu? I'm hoping I can keep my / folder on the 10GB drive and put any partitions that take up a lot of space on the 80GB. I've spent a lot of time cutsomizing my install and configuring the hardware, and essentially, I don't want to have to do it all over agian. Is this possible? And if so, how would I go about doing it?

---

### Post by peabody on 2006-08-07
An easy and typical way to do this without having to repartition and reinstall is via link farming.  Partition and format the new filesystems, then mount the linux filesystem somewhere (/mnt, /opt, anywhere you fancy).  You'll also want to edit the /etc/fstab so that this drive is always mounted there (not sure if this can be done under the disks control panel).  As root, create a folder on the new filesystem, probably with your username (sudo mkdir /mnt/newdrive/me), though the name doesn't really matter.  Change ownership of this folder to your user (sudo chown me.me /mnt/newdrive/me).  Then create a symbolic link in your home folder that points to this new folder (ln -s /mnt/newdrive/me /home/me/newdrive).  Then when you want to store information on the new drive, just make sure it's under the newdrive folder in your home directory.

You're still restricted to having all your settings and system software on the old 10Gig drive.  For most purposes that shouldn't be a problem (as I imagine you'd probably only use the new drive to store large things such as mp3 collections and video files).  However, if you'd like to use the new drive to store new software you install through apt, etc. it can be done using a similar link farming technique, but it'll have to be done via the rescue system since you're going to have to copy the old /usr over to the new drive, remove the old /usr, create a symlink on / to the new /usr, etc. , etc.  If you don't have experience copying lots of files and preserving their file attributes (something that is VERY important for this kind of operation) from the shell you will probably want to get a Unix guy to help you with this.

And then, of course, you could just backup, repartition reinstall, but I was under the impression you were trying to avoid that route.

---

### Post by kd5kij on 2006-08-07
Thanks for replying so quickly! 

Since I do want to have the freedom to install new software, and don't know exaclty where the files go or how to link them over to the new drive, I've decided maybe a fresh install is the way to go...

If I were to backup my system, would there be any way to preserve all the hardware configuration I've done? (ndiswrapper, 3D Video, etc....) It's seems I've read somewhere I can export a list of all my installed apps that I can re-apply using apt under the new install, but I don't remember where. But I do remember spending 4 days making ndiswrapper and wpa_supplicant work. I'd like to avoid that if possible. Could be as easy as just copying config files?

Thanks for the help. :)

---

### Post by peabody on 2006-08-07
There are two places where configuration is kept; user configuration is under your home folder in folders that start with a period (hidden folders and files).  All you need to back that up is to backup your home folder (including all hidden folders and files, VERY important that).  Then when you reinstall, copy everything over to the new user folder, replacing what's currently there.

System-wide configuration is stored in /etc and backing that up is trickier as you won't want to copy the whole thing verbatim because some stuff will be different under the new install (for instance your /etc/fstab will definitely be different).

Off of the top of my head I'm not sure where ndiswrapper keeps its configuration but I'm sure someone can help with that.  Once you know where it's stored, you simply need to back it up, then copy it over after the new install.

Also, just in case you don't feel like downloading every debian package that's on your current system for a second time, /var/cache/apt/archives should have all the debs that have been updated on your current system (provided you haven't purged this cache using apt-get).  If you back this up, you can then use gdebi or dpkg from the command line to install these packages BEFORE you attempt an update, which should restore your system to a state very similar to the way you had it before.

---

### Post by kd5kij on 2006-08-07
Thanks so much! This is sounding better all the time. How can I ensure that I backup all the hidden files and folders in my home directory? Will Ctrl + H to show them and then copy it to a DVD do it?

---

### Post by peabody on 2006-08-07
> **kd5kij said:**
> Thanks so much! This is sounding better all the time. How can I ensure that I backup all the hidden files and folders in my home directory? Will Ctrl + H to show them and then copy it to a DVD do it?

Yep, that should do it.  Double check and make sure you can see all the files that start with a period in their name once you've burned the DVD (this is all that's necessary to mark a file as "hidden" in unix-like OSes).

---

