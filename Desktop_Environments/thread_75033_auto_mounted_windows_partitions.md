---
title: "auto mounted windows partitions?"
date: 2005-10-13
forum: Desktop Environments
---

### Post by wilhlm on 2005-10-13
Hello

I think I would like to try out Ubuntu as a work environment, but I have all my documents on a windows partiton. In the new release, will these partitions automatically appear in file system? I know that it is possible to access them with the help of programmer commands, but I'm not up to that.

Thanks for any info on this..

---

### Post by davmac on 2005-10-13
I don't think they appear autoimatically, but it is quite easy to set up so that they're auto-mounted every time you start up.

Have a look at [http://ubuntuguide.org/#windows](http://ubuntuguide.org/#windows)

HTH,

Dave Mac

---

### Post by machaval on 2005-10-13
Hi man yes you can mount windows file system using the mount command or you can add the line /etc/fstab and it will mount it automatically when ubuntu starts
Saluti my friend
Mariano A.

---

### Post by manicka on 2005-10-13
From memory when I installed breezy a month or so a go, fat32 partitons are automatically configured but not ntfs

---

### Post by wilhlm on 2005-10-13
Hi folks

Thanks a lot for a quick reply and the info linked to and given here. I might try that, but I am a bit disheartened by earlier attempts to make things work. It usually takes alot of time and never works in the end anyway.

If technically possible, it might be a good idea to just have them appear as disks in the finder like on windows. I think I will present this as an idea for the next release in the appropriate forum.

But I may try, and now I have info on how to proceed. Thanks again.

---

### Post by valter on 2005-10-13
New Ubuntu has a GUI (Graphical user interface) for mounting partitons (look menus) :) tried it in live-cd and it worked

---

### Post by kombipom on 2005-10-13
Below is a copy of my /etc/fstab file to show you what one looks like that auto-mounts 2 windows partitions, one ntfs (XP) which is read only and one fat which is read-write so it can be used to move or share stuff between the two systems.  
Open for editing using      sudo gedit /etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda7       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda6       /boot           ext3    defaults        0       2
/dev/hda8       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1       /mnt/win_xp     ntfs    defaults,ro     0       0
/dev/hda5       /mnt/win_d      vfat    defaults,umask=000        0       0

You can find out what is on what partition by looking at System->Administration->Disks and looking at the Partitions tab. This will help you pick the right /dev/????.

The umask=000 lets all users write to the vfat partition (disk D in windows).  Last thing I heard it wasn't safe to write to ntfs so use the ro (read only) option.

Hope this helps.

Kombipom

---

### Post by xeta on 2005-10-13
Or, we could all love the trusty Wiki!

From: [https://wiki.ubuntu.com/AutomaticallyMountMSWindowsPartitions?highlight=%28partition%29](https://wiki.ubuntu.com/AutomaticallyMountMSWindowsPartitions?highlight=%28partition%29)


Mounting partitions with the script
Script assumptions

    *

      /media/ is an acceptable location for the partitions to be mounted

Acquiring the script

The script must be downloaded before it can be used. Type the following lines.

cd
wget [http://www.ubuntulinux.nl/files/winmac_fstab](http://www.ubuntulinux.nl/files/winmac_fstab)

The file winmac_fstab will now be in the current user's home directory.
Using the script

The script is non-interactive, and usage is simple. Type the following lines.

chmod u+x winmac_fstab
sudo ./winmac_fstab

This will make the script executable, then execute it with administrative rights.

The script will generate some output, regardless of whether it succeeds or not.
Cleaning up

The script is no longer needed, so type the following line to get rid of it.

rm winmac_fstab

All partitions on the system should now be accessible.

To verify access, open Gnome's file manager and direct it to /media/, which can be found by clicking the 'File System' location, and then double-clicking 'media'. Double-click any partition to be examined. If it contains files, the modifications were successful. If no files are found, read the next section.

If the script worked for you, don't stop reading yet! Some tips exist at the end of this article in the Hints, Tips, and Technical Information section to help make your Ubuntu experience even more enjoyable.

---

### Post by Wolki on 2005-10-13
[QUOTE=valter]New Ubuntu has a GUI (Graphical user interface) for mounting partitons (look menus) :) tried it in live-cd and it worked[/QUOTE]

I had some problems with that utility when I tried it some time ago, mostly stuff with permissions. 
However, the ubuntu install will suggest mount places for existing partitions during the partitioning step, so the fstab should be filled from the beginning.

---

### Post by ygarl on 2005-10-13
Yup!
New shiny Breezy just mounts them, and the end up quite nicely in the Places menu next the the System menu...

Also Gnome puts the Icons on my desktop for me. It's almost like XP, but without huge bloatware, viruses, with auto-updating software and a non-crashing OS!

---

