---
title: "Ubuntu Loading Splash Screen Gone!"
date: 2009-03-03
forum: General Help
---

### Post by murmini on 2009-03-03
I have three Ubuntu machines running 8.10 and mysteriously, they all seem to have lost their sliding bar splash screen that normally runs when Ubuntu starts. All three machines are up to date with the latest updates - is that in fact the problem and an update has some how turned this off? Any help would be appreciated.

---

### Post by Psyrix on 2009-03-03
Have you downloaded startup-manager? if not you could try using that to manage your splash screens, or install a custom Usplash screen.

sudo apt-get install startup-manager

---

### Post by grinby on 2009-03-03
I'm having the same "problem."  It is a little weird that now it shows the status bar bouncing back and forth then switches to verbose mode at "Reading Files Needed to Boot."

Startup Manager didn't do it for me, but if you want to try it, the command would be sudo apt-get install startupmanager.

---

### Post by murmini on 2009-03-04
I tried the startup manager and it didn't seem to make any difference. I am intrigued as to what has suddenly caused this to happen.

---

### Post by 67GTA on 2009-03-04
Open a terminal and run ```
sudo blkid
``` This will show the UUID's of the partitions on your machine. Then check that the UUID for your swap partition matches the ones in /etc/fstab and /etc/initramfs-tools/conf.d/resume.

---

### Post by rbolio on 2009-03-04
can it be something related to the ##.13 kernel released recentley?

---

### Post by murmini on 2009-03-05
> **67GTA said:**
> Open a terminal and run ```
sudo blkid
``` This will show the UUID's of the partitions on your machine. Then check that the UUID for your swap partition matches the ones in /etc/fstab and /etc/initramfs-tools/conf.d/resume.

I tried his and the results are identical and match.  What else can I try?

---

### Post by murmini on 2009-03-05
Upon further research I have found that the same machine that was not showing the splash screen does when I install a different hard drive with an identical install of ubuntu on it. So all that has changed is the drive and the installed version (same identical version)- then the splash screen shows.

---

### Post by 67GTA on 2009-03-05
Hard to say from here. Can you post the output of these commands from a terminal? Also check that /etc/usplash.conf has the correct resolution for your monitor.

```
free
sudo fdisk -lu
sudo blkid -c /dev/null
cat /etc/fstab
cat /etc/initramfs-tools/conf.d/resume
apt-cache policy usplash
```

---

### Post by murmini on 2009-03-05
awol@awol-desktop:~$ free
             total       used       free     shared    buffers     cached
Mem:        505524     491252      14272          0      14808     173424
-/+ buffers/cache:     303020     202504
Swap:       738948       1316     737632
awol@awol-desktop:~$ sudo fdisk -lu
[sudo] password for awol: 

Disk /dev/sda: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders, total 39102336 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x57575757

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    37624229    18812083+  83  Linux
/dev/sda2        37624230    39102209      738990    5  Extended
/dev/sda5        37624293    39102209      738958+  82  Linux swap / Solaris
awol@awol-desktop:~$ sudo blkid -c /dev/null
/dev/sda1: UUID="aac38e34-7177-4471-9431-9ef8ac22ff88" TYPE="ext3" 
/dev/sda5: UUID="2a2676b1-436d-4044-b97f-6bdbdd281fa7" TYPE="swap" 
awol@awol-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=aac38e34-7177-4471-9431-9ef8ac22ff88 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=2a2676b1-436d-4044-b97f-6bdbdd281fa7 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
awol@awol-desktop:~$ cat /etc/initramfs-tools/conf.d/resume
RESUME=UUID=2a2676b1-436d-4044-b97f-6bdbdd281fa7
awol@awol-desktop:~$ apt-cache policy usplash
usplash:
  Installed: 0.5.25
  Candidate: 0.5.25
  Version table:
 *** 0.5.25 0
        500 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid/main Packages
        100 /var/lib/dpkg/status

---

### Post by 67GTA on 2009-03-05
Everything looks fine there. Have you upgraded to Intrepid, or is this a new install? Have you changed anything recently? Kernel upgrade? You might try updating your initrd image. You can find your "kernel version" with ```
uname -r
```:

```
sudo update-initramfs -u -k "kernel-version" 
```

---

### Post by murmini on 2009-03-05
Thank you for all the help.  I am convinced it is related to the vide card not being able to display the usplash image at startup as the drivers are not loaded.  So I went into the bios and the only video setting I could modify was "VideoRam = 1Mb" and the only option was changing it to "VideoRam=8Mb"  Viola !  It fixed it.  On the other two machines I also tried downloading the application StartUpManager and after turning the "Show Splash Screen" off, then re-opening the app and setting it to On... It fixed it.  Not a perfect fix - and I really would like to understand what is going on.  In answer to your question, these are installs from the downloaded 8.10 disk without any updates and then with all the 246 updates.  Again - Thanks for the help.

---

### Post by dcstar on 2009-03-05
> **murmini said:**
> Thank you for all the help.  I am convinced it is related to the vide card not being able to display the usplash image at startup as the drivers are not loaded.  So I went into the bios and the only video setting I could modify was "VideoRam = 1Mb" and the only option was changing it to "VideoRam=8Mb"  Viola !  It fixed it.  On the other two machines I also tried downloading the application StartUpManager and after turning the "Show Splash Screen" off, then re-opening the app and setting it to On... It fixed it.  Not a perfect fix - and I really would like to understand what is going on.  In answer to your question, these are installs from the downloaded 8.10 disk without any updates and then with all the 246 updates.  Again - Thanks for the help.

If the /etc/usplash.conf resolution is changed from the default to a larger value that your video card cannot display (unless it has sufficient RAM) then the splash screen will not be seen.

Changes to that file will not affect the **login** usplash until update-initramfs is run (like when a new kernel is installed), but they will be seen immediately on the logout usplash screen.

---

### Post by murmini on 2009-03-05
Yes, this is beginning to make sense to me now... I will experiment some more. Thanks for your help and guidance.

---

### Post by djodjoman on 2009-06-21
[http://ubuntuforums.org/showthread.php?p=7491821#post7491821](http://ubuntuforums.org/showthread.php?p=7491821#post7491821)

Same issue here, annoying!

---

