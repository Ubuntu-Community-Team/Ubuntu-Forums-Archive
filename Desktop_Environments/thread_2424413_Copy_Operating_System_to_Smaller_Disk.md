---
title: "Copy Operating System to Smaller Disk"
date: 2019-08-08
forum: Desktop Environments
---

### Post by Geoff_Lane on 2019-08-08
Folks,

Is there a way to copy an operating system to a smaller disk?

Appreciate used space would have to be less than capacity of destination disk but with the popularity now of SSDs many are considering the switch. As the capacities on SSDs are still smaller than conventional disks I don't think Macrium Reflect or Clonezilla can do this.

I'm guessing maybe gparted to reduce disk/partition size then copy over. Can't think of any other way.

Geoff

---

### Post by oldfred on 2019-08-08
You already changed to [Solved]?

I always suggest new clean install. 
And restore data like /home, list of installed apps and anything else important. 

Clean install does a major housecleaning which most users have not done. And restoring from backup becomes a good way to test that your backup procedure is correct & complete as you still have old drive to go back to in case you are not including everything you want.

---

### Post by TheFu on 2019-08-08
If you use a file-based backup strategy, this should work fine.  My backups work this way and assume the new machine will be a fresh install with minimal packages (usually just ssh-server), so the boot issues and fstab issues are handled by the fresh installer.  Just setup the partitions as you like using "do something else" in the installer.  Easy-peasey.  
Takes about 30-45min to restore from backups to get a machine nearly identical to what was backed up.  I do not backup the entire OS.  I've posted my list of directories and a few extra steps in these forums multiple times for what to be backed up.  Look for "apt-mark", "rdiff-backup" and my userid in the search.  If you use LVM, this backup method has ZERO downtime.

Also, **fsarchiver** will allow restoring partitions to smaller partitions.  You will need to install/fix grub and definitely need to fix the /etc/fstab manually from a live-boot environment. Once you know how to do those 2 things, it is a 3-5 minute task after restoring everything.  If you use LVM, this backup method has ZERO downtime.  If you don't, then it is important to boot from alternate media to create the partition images.  fsarchiver is smart like clonezilla and if you script it, then you'll be certain to have consistent, compressed, images.  It is smarter for file systems it knows about, but can handle "unsupported" file systems by just copying bytes and compressing as it is written to disk.  I've used it to move from 64G storage to 16G storage.  For MS-Windows, this is the tool I use.  It doesn't care of the partition is encrypted or not. Works either way, just with less compression resulting for encrypted stuff.

Lots of people use clonezilla. I've always found it to be confusing.  Probably user error on my side.

My notes on fsarchiver:```

# #################################################
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      499711      248832   83  Linux
/dev/sda2          501758   250068991   124783617    5  Extended
/dev/sda5          501760   250068991   124783616   83  Linux

# Backup entire root-LV
/usr/sbin/fsarchiver  -vA -z5 -j2 savefs \
   /media/tf/c720-stuff/c720-15_05_25.fsa \
   /dev/mapper/lubuntu--vg-root

# Restore root-LV
/usr/sbin/fsarchiver restfs /media/tf/c720-stuff/c720-15_05_25.fsa \
        /dev/mapper/lubuntu--vg-root
```

The LV device could be a specific partition, if you like on either or both sides.

---

