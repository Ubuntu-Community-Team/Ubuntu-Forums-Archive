---
title: "subfs?"
date: 2005-12-08
forum: Desktop Environments
---

### Post by CharlieC on 2005-12-08
When I try to mount a blank dvd or cd in my dvd burner this is the error I get:
cc@ubuntu:/$ sudo mount /dev/cdrom1 /mnt
mount: you must specify the filesystem type
Here is what is in fstab:
/dev/hdd             /media/cdrom1        subfs      user,noauto
When I try dvd:rip I can read the titles and the get the error:
Failed to mount DVD at /dev/cdrom1 Mount unknown file system type subfs.
I have tried every combination I can find for /dev/cdrom1, in fstab it is /dev/hdd. Always the same error. 
I have googled this to death. It seems there are others who have had this problem but I could not find any solution.
Maybe a blank cd/dvd is supposed to do this. If so ripping dvd's isnt going to be easy and it is the only thing that I cant do on Ubuntu 5.10 that I can do on windows.
Any suggestions would be greatly appreciated.

TIA
Charlie

---

### Post by Ampersand on 2005-12-08
Try changing subfs in fstab to udf,iso9660

---

### Post by CharlieC on 2005-12-08
Hi;

    I appreciate the response but unfortunately it did not work out. That is what I read a lot of while googling.
   Part of the problem with DVD:Shrink is when I check the preferences, I see that the cdrecorder drive has an error which I am unable to fix. Essentially the error is:
CD recorder device (n,n,n, or filename) 0,X,0 has not format n,n,n and is no file:not OK.
   I actually cleard the error one time still using /dev/cdrom1 but it keeps comming back. BTW I had this error in the past and swapped out the dvdrecorder drive and it is still the same so I doubt it is hardware.
    When I try to mount the drive in a terminal I get the same error as before.

Charlie

---

