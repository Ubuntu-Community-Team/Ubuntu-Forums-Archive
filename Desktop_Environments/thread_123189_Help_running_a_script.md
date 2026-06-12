---
title: "Help running a script"
date: 2006-01-29
forum: Desktop Environments
---

### Post by deity_me on 2006-01-29
I have hundreds of CDs that need their contents copied to a hard drive
now i dont want to sit there all day mounting and unmounting and doing a 
cp -R /media/cdrom0/* /media/hdb1/
umount /media/cdrom0
eject

all day
I just want to pop it in an it'll mount, copy and when finished umount and eject wait for the next CD to begin the process all over again until all these CDS i made years ago are copied to the hard drive so i can then burn them again on DVDs

I almost found a way but ran into a little glitch
That media storage thingy where upon insertion of a media you can make it take certain actions
well i tried putting 
copy -R /media/cdrom0/* /media/hdb1; umount /media/cdrom0; eject;
into a script and then have it run that script 

but i get an error 
/media/cdrom0 is a folder, but a file was expected

also same thing happens when i put this directly in the command to execute instead of going to a execute a script

this lazy guy needs help

---

### Post by ardchoille on 2006-01-29
[QUOTE=deity_me]I have hundreds of CDs that need their contents copied to a hard drive
now i dont want to sit there all day mounting and unmounting and doing a 
cp -R /media/cdrom0/* /media/hdb1/
umount /media/cdrom0
eject

all day
I just want to pop it in an it'll mount, copy and when finished umount and eject wait for the next CD to begin the process all over again until all these CDS i made years ago are copied to the hard drive so i can then burn them again on DVDs

I almost found a way but ran into a little glitch
That media storage thingy where upon insertion of a media you can make it take certain actions
well i tried putting 
copy -R /media/cdrom0/* /media/hdb1; umount /media/cdrom0; eject;
into a script and then have it run that script 

but i get an error 
/media/cdrom0 is a folder, but a file was expected

also same thing happens when i put this directly in the command to execute instead of going to a execute a script

this lazy guy needs help[/QUOTE]
You are trying to umount the /media/cdrom0 folder when you should be umounting the device itself. This should work:

cp -R /media/cdrom0/* /media/hdb1; umount /dev/cdrom0; eject;

---

### Post by deity_me on 2006-01-29
Nope
cant get to the copy stage
still same error message
tried just
cp -R /media/cdrom0/* /media/hdb1
and still the same

---

### Post by cwaldbieser on 2006-01-29
[QUOTE=deity_me]Nope
cant get to the copy stage
still same error message
tried just
cp -R /media/cdrom0/* /media/hdb1
and still the same[/QUOTE]
What do you get if you try:
```

$ echo cp -R /media/cdrom0/* /media/hdb1

```
That will cause the shell to show you what it is expanding your command to (with the wildcard).  The only think I can think of is that there is some sort of symbolic link being followed back to /media/cdrom0.

---

### Post by ardchoille on 2006-01-29
[QUOTE=deity_me]Nope
cant get to the copy stage
still same error message
tried just
cp -R /media/cdrom0/* /media/hdb1
and still the same[/QUOTE]
I don't know about the copy bit, I wasn't doing anything with that. I was just trying to solve your error when you tried to umount a folder :)

hdb is usually a cd-rom device. Is that the case? if not, is hdb1 mounted?

---

### Post by cwaldbieser on 2006-01-29
[QUOTE=ardchoille]I don't know about the copy bit, I wasn't doing anything with that. I was just trying to solve your error when you tried to umount a folder :)

hdb is usually a cd-rom device. Is that the case? if not, is hdb1 mounted?[/QUOTE]
Actually, I seemed to recall that you should be able to use the device or the mount point to unmount.  I looked it up in the man pages:
> 
The  umount command detaches the file system(s) mentioned from the file
       hierarchy.  A file system is specified by giving the directory where it
       has  been  mounted.  Giving the special device on which the file system
       lives may also work, but is obsolete, mainly because it  will  fail  in
       case this device was mounted on more than one directory.

So it seems that giving the directory is actually the preferred way to umount.  You learn something new every day, I guess!

---

