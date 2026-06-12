---
title: "problem with a hard drive"
date: 2006-08-28
forum: Desktop Environments
---

### Post by tomslopez on 2006-08-28
I installed ubuntu and I formatted a second hard drive as ext3 and I mounted it by creating a folder /home/fede as the access path, then I edited the fstab adding a line with the info. of the hard drive,
```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/hda1           /                       ext3    defaults,errors=remount-ro   0         1
/dev/hdb	    /home/fede	      ext3	 defults	     0	            2
```
it mounted fine but when I restart my computer when its loading when it reaches the checking all filesystems it jumps to a black screen with white letters and it says:
```
fsck.ext3: Bad magic number in super-block while trying to open /dev/hdb
/dev/hda: (and some other stuff)
The super block could not be read or does not describe a correct ext2 filesystem.
If the device is valid and it really contains an ext2 filesystem (and not swap or ufs or something else),
then the superblock is corrupt, and you might try running e2fsck with an alternative superblock:
e2fsck -b 8193<DEVICE>
root@Federico: # exit from this shell and continue system startup.
```
this code is not exactly how it appears but its pretty close, at that point where it says exit from this shell and continue startup I hit ctrl+d to continue to startup and it continues normally. So my question is what can I do to not get all that everytime I turn on my computer?
Any help is greatly appreciated.
Thank You.

---

### Post by orb9220 on 2006-08-28
Shouldn't all hd's have a number like hdb1 instead of:

/dev/[COLOR="Cyan"]hdb[/COLOR]	    /home/fede	      ext3	 defults	     0	            2

And change the 2 to 0 if you want to disable hd checking on boot up. But you will probally want to keep it on.

recheck the partion with rescue cd and gparted to see if it is a valid partition,

---

