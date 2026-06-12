---
title: "Change Home Directory problems"
date: 2012-03-31
forum: Desktop Environments
---

### Post by neuman1812 on 2012-03-31
I'm trying to move my /home directory to a second drive.   I Followed the directions here 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

On bootup I get an error message stating that it can't mount /media/home 

This is my boot.log with the errors.  

```
fsck from util-linux 2.19.1
fsck from util-linux 2.19.1
/dev/sda1: clean, 230942/4759552 files, 15993692/19013376 blocks
2nd_Drive: clean, 4750/7634944 files, 644822/30517467 blocks
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

mountall: mount /media/home [819] terminated with status 32
mountall: Filesystem could not be mounted: /media/home
Skipping /media/home at user request
Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
 * Starting AppArmor profiles       [80G 
[74G[ OK ]
 * Setting sensors limits       [80G 
[74G[ OK ]
xhost:  unable to open display ""
xhost error ignored, GPU computing may not be possible * Stopping Failsafe Boot Delay[74G[ OK ]
 * Stopping System V initialisation compatibility[74G[ OK ]
 * Starting System V runlevel compatibility[74G[ OK ]
 * Stopping automatic crash report generation[74G[[31mfail[39;49m]
 * Starting CPU interrupts balancing daemon[74G[ OK ]
 * Starting deferred execution scheduler[74G[ OK ]
 * Starting regular background program processing daemon[74G[ OK ]
 * Starting LightDM Display Manager[74G[ OK ]
 * Starting ACPI daemon[74G[ OK ]
 * Starting anac(h)ronistic cron[74G[ OK ]
 * Starting save kernel messages[74G[ OK ]
 * Starting BOINC core client: boinc       [80G 
[74G[ OK ]
 * Setting up scheduling for BOINC core client and children:       [80G 
[74G[ OK ]
Starting polipo:  * Starting CUPS printing spooler/server[74G[ OK ]
polipo.
 * Stopping save kernel messages[74G[ OK ]
 * Stopping anac(h)ronistic cron[74G[ OK ]
```

This is my Fstab
```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=eb614458-8188-449e-8d39-5c5335fc0aee /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=430c8f10-cd31-464b-9efc-86298a4192b8 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
# (identifier)  (location, eg sda5)   (format, eg ext3 or ext4)      (some settings) 
UUID=2cba9a81-a3f2-464d-964c-3bb0946c530b   /media/home    ext3          nodev,nosuid       0       2 

```

---

### Post by Bucky Ball on 2012-03-31
```
# (identifier)  (location, eg sda5)   (format, eg ext3 or ext4)      (some settings)  UUID=2cba9a81-a3f2-464d-964c-3bb0946c530b   /media/home    **ext3**          nodev,nosuid       0       2
```Is it an EXT3 partition or EXT4? Might be a silly question but you never know ...

Also wondering what 'nodev,nosuid' are there for ...

My entry for /home looks like this:

```
UUID=0cdd1989-6b0d-48fe-a5a8-2b8ae640dcc1       /home   ext4    defaults        0       2
```

I would just change that to '/media/home' if I was mounting it in /media.

---

### Post by neuman1812 on 2012-03-31
ahh crap.... So I just looked at my fstab again...

the new line 
```
# (identifier)  (location, eg sda5)   (format, eg ext3 or ext4)      (some settings) 
UUID=2cba9a81-a3f2-464d-964c-3bb0946c530b   /media/home    ext3          nodev,nosuid  
```

I copied directly from the website....Dummy me I didnt change it...

It should be ext4... 

the nodev,nosuid im not sure on..  but I will look them up.

---

### Post by Bucky Ball on 2012-03-31
Use mine and see how that goes. Just change it to:

```
UUID='your_correct_uuid'      /media/home   ext4    defaults        0       2
```

---

### Post by neuman1812 on 2012-03-31
OK..So i think i farked this up somehow...  thoes original directions I had screwed me up.   I wish there was A way, like windows.  where I can just right click..change directory location.  


Output of blkid
```
/dev/sda1: UUID="eb614458-8188-449e-8d39-5c5335fc0aee" TYPE="ext4" 
/dev/sda5: UUID="430c8f10-cd31-464b-9efc-86298a4192b8" TYPE="swap" 
/dev/sdb1: LABEL="250gb" UUID="2cba9a81-a3f2-464d-964c-3bb0946c530b" TYPE="ext4"
```

What Im trying to do is mount my home directory in the "250gb" drive... its a seperate drive completly from my boot drive..

My fstab is currently 
```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=eb614458-8188-449e-8d39-5c5335fc0aee /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=430c8f10-cd31-464b-9efc-86298a4192b8 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

```

I know i have to put a new UUID= line in there ..But I just cant seem to get it right.Any help would be good.

---

### Post by Bucky Ball on 2012-03-31
> **Bucky Ball said:**
> Use mine and see how that goes. Just change it to:

```
UUID='your_correct_uuid'      /media/home   ext4    defaults        0       2
```

Did you try it???

---

### Post by Bobhuber on 2012-03-31
> **neuman1812 said:**
> OK..So i think i farked this up somehow...  thoes original directions I had screwed me up.   I wish there was A way, like windows.  where I can just right click..change directory location.  



First of all make a directory.
sudo mkdir /media/home
Then add the following to your fstab file.
/dev/disk/by-uuid/2cba9a81-a3f2-464d-964c-3bb0946c530b /media/home    ext4 nodev,nosuid 0 2

Then follow the rest of the directions on the site.
Good luck.

---

