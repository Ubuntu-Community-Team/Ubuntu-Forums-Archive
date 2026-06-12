---
title: "formatting issues"
date: 2009-01-21
forum: General Help
---

### Post by anechoic on 2009-01-21
- I have a barebones mini9 with 512M RAM and a 4G SSD
- I've purchased a 2G RAM card
- I also plan on purchasing a 32G SSD this week
- I've installed 8.10 w/ no swap space, 2 partitions: /home and  
root , ext2 filesystem

- since I am buying a bigger SSD this week I want to backup my mini9  
drive onto a 250G USB hard drive then restore it onto the 32G when it  
comes in

- but I've got this weird problem:
   - I formatted the drive this way:
   - using Gparted I unmounted the drive
   - formatted it as an ext2 file system - since FAT32 max file size is 4G and my tar backups will most likely be larger than this
   - not being able to remount it via Gparted I unplugged it and  
plugged it back in
   - it showed up on the desktop
   - using the file browser I tried to make a dir called 'backup' but the 'create folder' selection was grayed out
   - the /media/driveForBackup/ dir had a lock on it
   - I was able to sudo mkdir on the drive

but I am not able to back up on it using 'sbackup' since the backup dir is locked
q1: do I just change the owner with chown?
q2: why does Gparted create a drive partition that is owned by root
and not by the user logged in? am I doing something wrong here?
q3: since I am only backing and restoring up '/home/' will everything be restored to its current state (i.e. new apps, utilities, environment settings, etc) after installing a new system on the 32G SSD?

all links, pointers, suggestions, enlightenment appreciated
:)

---

### Post by vanadium on 2009-01-21
> 
q1: do I just change the owner with chown?


Yes, but you must act with root privileges (aka: 'sudo chown ...'.
> 
q2: why does Gparted create a drive partition that is owned by root
and not by the user logged in? am I doing something wrong here?

This is the safety model of unix/linux. The user should never care about partitions and mounting. That is a matter of the root. It is also up to the root user (or the user with root privileges) to assign ownership and permissions. You did nothing wrong.

> 
q3: since I am only backing and restoring up '/home/' will everything be restored to its current state (i.e. new apps, utilities, environment settings, etc) after installing a new system on the 32G SSD?

Not new apps, because the root installs apps. However, all your configuration settings for apps will be preserved.

Copying a /home directory might not be trivial. This page [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome) suggests a complicated command for copying a home partition: apparently a plain "cp -a" or "rsync -a" might not be sufficient to copy and preserve all features of a home directory.

---

### Post by anechoic on 2009-01-22
yes thanks I know about sudo and being root :)

but I still want to know why after formatting a drive - the way I described it in my original post - I am unable to back up to it since it is locked - i.e. why is there no way to change this in Parted?it seems like a crucial detail to leave out of any instructions on formatting a new disc.

and also what is the best method to make an image of a drive so I can restore it to a new empty drive later?

---

### Post by sedawk on 2009-01-22
Have a look at the tool "rsync". You can use it to create a
"perfect mirror" of your home directory on another disk without
creating a huge tar archive.
Example:
```

rsync -av /home /media/DriveForBackup/

```
This will create a "home" directory in /media/DriveForBackup/ and
copy everything.
Appending a slash to "/home" changes the behaviour:
```

rsync -av /home /media/DriveForBackup/

```
Now everything below "/home" is copied but not home itself.

If there are problems with permissions run rsync as root by
appending a "sudo " in front of the command.
Always use the "-n" option for testing it tells you what it
would do but doesn't change anything.

And rsync even works over the network (e.g. using ssh protocol), so you can
backup to another computer.

---

### Post by vanadium on 2009-01-22
> I still want to know why after formatting a drive - the way I described it in my original post - I am unable to back up to it since it is locked - i.e. why is there no way to change this in Parted?
That was what I was trying to explain. Things in linux are designed with "safety" in mind. The normal user has no business with partitioning, formatting and granting permissions.

By the way, sedawk is providing the excellent suggestion of backing up your valuable user data using rsync. The first time, it takes a long time, but the next update of your backup will take 10 - 15 seconds. There is no reason anymore to not have a daily backup copy of your data.

Way better than trying the complicated and time consuming creation of images.

---

### Post by anechoic on 2009-01-22
testing with rsync now but getting fail messages due to chown perms
I guess rsync won't back up all files...?

---

