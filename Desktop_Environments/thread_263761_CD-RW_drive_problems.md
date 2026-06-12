---
title: "CD-RW drive problems"
date: 2006-09-23
forum: Desktop Environments
---

### Post by Ciego on 2006-09-23
I have had no luck finding solutions in other threads so if you have any ideas, please let me know.  

I am having dificulties getting my CD-RW drive to work.  When I try to use it, I get an error that says that I am unable to mount the selected volume ... along with this

mount: no medium found

mount: no medium found

error: could not execute pmount



Here is my fstab file.  I know from other posts that this is somehow related to my probelem, but I do not know exactly what I need to add to the file.  I also do not know the significance of the spaces in the file .... do they matter?

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

I am sure that this needs to be edited because my CDRW drive is /dev/hdd and I do not see it in this file.  I tried tinkering with it a bit but then I just had more errors so I restored the original file.

I am using this kernel 
```
~$ uname -r
2.6.15-27-386

```
Running Ubuntu Dapper


Let me know if any other outpputs would be helpful.

---

### Post by orb9220 on 2006-09-23
> I am sure that this needs to be edited because my CDRW drive is /dev/hdd

And where did you get the idea? Since mine is hdc too.

/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

and works.

---

### Post by Ciego on 2006-09-23
I also have a CD-ROM in my setup it is /dev/hdc. My CD-RW is /dev/hdd

I know that it needs to be edited because /dev/hdd is not even in the file.  I do not know exactly what I am supposed to put in there though.

I found that in the device manager. The CD-RW is the slave and the CD-ROM is the master.

---

### Post by Ciego on 2006-09-23
By the way ...thanks for the tip on getting my keyboard to work. (from this thread [http://www.ubuntuforums.org/showthread.php?t=224394](http://www.ubuntuforums.org/showthread.php?t=224394))  I installed that Keytouch program and everything is working fine now.

---

### Post by christhemonkey on 2006-09-23
Add this line to the bottom of your /etc/fstab:
```
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0 
```

Something like that anyways.

---

### Post by orb9220 on 2006-09-23
Well did you try changind the hdc to hdd in fstab then reboot?

If it dosn't work then remember to change it back.

And that is all I can think of at the moment as I am still trying to get my cafiene or cafeine or Kafeine? level up to concious level.

---

### Post by Ciego on 2006-09-23
I added that line to my /etc/fstab and now I get this error.

mount: mount point /media/cdrom1 does not exist

---

### Post by Ciego on 2006-09-23
OK .... I figured out that I had to make the directory first, but now the error is coming back saying that no medium is found.  I tried differnt discs and still nothing.

---

### Post by bodhi.zazen on 2006-09-23
orb9220: He has 2 CD-ROM drives.

Try this:```
/dev/hdd  /media/cdrom1  iso9660  ro,user,noauto 0  0
```
In fstab.

---

### Post by Ciego on 2006-10-01
I still have not found a solution to this problem.  Anyone have any other idea?  Anyone know of any guides that may cover this?

---

### Post by christhemonkey on 2006-10-01
Just checking that you do have a cd in the drive?

Hate to point out the obvious as well.


Can you give us the result of dmesg after you get this error?
```
dmesg | tail 
```

---

### Post by Ciego on 2006-10-01
Here is the output I get

```
~$ dmesg | tail
[17184255.868000] cdrom: open failed.
[17184255.912000] cdrom: open failed.
[17184275.148000] cdrom: open failed.
[17184275.192000] cdrom: open failed.
[17200027.704000] cdrom: open failed.
[17200033.948000] cdrom: open failed.
[17200089.176000] cdrom: open failed.
[17200091.504000] cdrom: open failed.
[17200092.816000] cdrom: open failed.
[17200094.168000] cdrom: open failed.
```

---

### Post by Ciego on 2006-10-01
I am going to open up the case and make sure I have everything connected correctly.

---

### Post by Ciego on 2006-10-04
I have the CDROM and the CDRW on the same IDE cable with the CDROM at the end of the cable and the CDROM jumper in the master position. The CDRW is at the middle of the cable and the CDRW jumper is in the slave position.

This is my fstab file now:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   iso9660 ro,user,noauto     0       0

```

This is a list of my devices.  Both are pointing at hdd and I am assuming that is incorrect. 
```
~$ ls -al /dev/cd*
lrwxrwxrwx 1 root root 3 2006-10-04 19:29 /dev/cdrom -> hdd
lrwxrwxrwx 1 root root 3 2006-10-04 19:29 /dev/cdrw -> hdd

```

I change the symlink for the cdrom to point to hdc
```
~$sudo rm /dev/cdrom 
~$ sudo ln -s hdc /dev/cdrom

```

You can see the effect here when I list my devices again
```
~$ ls -al /dev/cd*
lrwxrwxrwx 1 root root 3 2006-10-04 20:50 /dev/cdrom -> hdc
lrwxrwxrwx 1 root root 3 2006-10-04 19:29 /dev/cdrw -> hdd

```

At this point, I have 
1. a symlink in /dev called cdrom that points to hdc
2. a symlink in /dev called cdrw that points to hdd
3. a file in /dev called hdc that has a drive icon
4. a file in /dev called hdd that has a drive icon
5. a symlink in /media called cdrom that points to /media/cdrom0
6. a symlink in /media called cdrw that points to /media/cdrom1
7. a folder in /media called cdrom0
8. a folder in /media called cdrom1

The drive still does not work and every time I reboot, the devices change back to where they both link to hdd.  

Is the fstab file correct? 
Why do the chages revert when I reboot?
How can I make the changes stay even when I do reboot?
Any other ideas? 
What am I missing?

Thanks again for the help.

---

### Post by IoCaster on 2006-10-05
Have you tried reversing the order of the drives on the ide cable. The burner really should be master. If you are using cable select try setting the cdrw on the end of cable and putting the jumper in the master position. It might be a hardware issue that's causing your grief.

---

### Post by Ciego on 2006-10-05
I have not tried swapping their locations on the IDE cable but I will surely give it a try.  I know that I need to adjust the jumper positions, but do I need to alter the fstab file or my symlinks when I do this?  Do you have any idea why my symlinks are reset each time I reboot?

---

### Post by IoCaster on 2006-10-05
> **Ciego said:**
> I have not tried swapping their locations on the IDE cable but I will surely give it a try.  I know that I need to adjust the jumper positions, but do I need to alter the fstab file or my symlinks when I do this?  Do you have any idea why my symlinks are reset each time I reboot?

I've had some problems in the past with cable select and drive positioning on ide chain. I'm fairly new to linux so I really can't help you with the symlink stuff. It could be something as simple as hardware detection occurs at bootup and rewrites a hwconfig based on what it detects from bios or something else. Good luck.

Regards - Joe

---

