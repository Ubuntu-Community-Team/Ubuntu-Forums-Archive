---
title: "can't resize paritions!  gparted won't let me do anthing :("
date: 2006-02-24
forum: Desktop Environments
---

### Post by magomago on 2006-02-24
Hi, I have 2 HDDS.  One Windows, the other Windows/Linux.  However the past few months I've been using ubuntu a LOT more and I want to grab more space off the drive that i'm sharing my storage space with and give it to Ubuntu.  Its an 80 with 15 to Ubuntu and 65 to windows.  of that 15 to ubuntu about 12 are used, and of that 65 about 20 are used.  
I tried using gparted but the only option that isn't blacked out is "delete partition"....which I don't want to do!  I tried unmounting the NTFS partition but it doesn't work 

the storage /dev/hde1
and linux is 
/dev/hde2 holding /dev/hde5 and /hde6 (swap)

can anyone tell me what I need to do so I can shrink windows a little bit (I need to make room for civ4! cedega supports it now :D)

---

### Post by lamego on 2006-02-24
I don't know about gparted, I did use qtparted a few times without problems.
You can always unmount the partition manually with:
```
sudo umount /dev/hde1
```

---

### Post by suRoot on 2006-02-24
Try DiskDrake.  Here's some info about it:

[http://www.ubuntuforums.org/showthread.php?t=114142](http://www.ubuntuforums.org/showthread.php?t=114142)

---

### Post by magomago on 2006-02-24
I would prefer an easier method than downloading an entire other distro.  If I did that I might was well get the security version of knoppix so I have a few more goodies open.  

As for not unmouning it, I'm sure it did because I could not access the drive.  Just for kicks I tried unmounting it through command line yet it didn't help anything

---

### Post by plors on 2006-02-25
use gparted on it's own [livecd]("http://gparted.sourceforge.net/livecd.php")

---

### Post by ardchoille on 2006-02-25
install gparted, it's in the repos.

---

### Post by CompShrink on 2006-03-01
Install ntfsprogs and then gparted can work with NTFS paritions. That's probably why you can't change your windows partion, assuming you already tried unmounting, which you can do through gparted's interface.

---

### Post by aysiu on 2006-03-01
[QUOTE=magomago]I would prefer an easier method than downloading an entire other distro.  If I did that I might was well get the security version of knoppix so I have a few more goodies open.[/QUOTE] It actually *is* worth downloading an entire other distro. Ubuntu's live CD is not intended to be a recovery / partitioning CD. It can be used as such, but that's not its ideal purpose.

And PCLinuxOS has plenty of goodies, and DiskDrake is far more reliable a partitioner than Knoppix's QTParted. I've **never** had an option greyed out in DiskDrake.

---

### Post by aoroberson on 2008-05-31
I guess it's better late than never. I had the same problem, turned out to be bad sectors (damaged disk) on hard drive not letting gparted run properly. If you have windows already installed you need to boot it up and run checkdisk like so.

1. Click the Start button then select Run
2. In the Run window's Open box, type cmd or command
3. Click OK and an MS-DOS-style black screen will appear in a new window
4. Run chkdsk by typing "chkdsk c: /f /r" without quotes and then press <Enter> 
5. A message will appear that says:"chkdsk cannot run because the volume is in use by another process. Would you like to schedule this volume to be checked the next time the system restarts? <y/n>"
6. Type y (for "yes") and then press <Enter>
7. A message will appear that will say: "This volume will be checked the next time the system restarts"
8. Type exit and then press <Enter> to close the MS-DOS-style black screen window
9. Reboot (restart) the computer as you normally would and chkdsk will automatically begin running after your reboot (restart). While chkdsk is running, you will see a light blue window with a dark blue band at the top and bottom. Chkdsk will display the specific stage it is checking as well as the percentage of completion of the stage. You cannot do anything else on your computer while chkdsk is running. When chkdsk is finished, it will automatically reboot (restart) your computer. 

Then, you can run gparted normally. Hope this helps a little.

---

