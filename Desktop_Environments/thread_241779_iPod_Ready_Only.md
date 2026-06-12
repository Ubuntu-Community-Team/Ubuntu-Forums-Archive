---
title: "iPod Ready Only"
date: 2006-08-22
forum: Desktop Environments
---

### Post by Sethro on 2006-08-22
I am just about ready to huk my iPod out the window lol.
Is their a fool proof method to get rid of ready only thing. Its really getting to me. I tried some of the tutorial but I keep on getting " Not Found" or something..

---

### Post by Sethro on 2006-08-22
Come on guys help me out here

---

### Post by Dubbayoo on 2006-08-22
WTF does 'ready only' mean?

---

### Post by Sethro on 2006-08-22
Whoops sorry *corrected* now how do i get thing to work??

---

### Post by Dubbayoo on 2006-08-22
once again wtf is ready only? complete sentences please, preferably english.

---

### Post by RAOF on 2006-08-23
To help you, we need to know what the problem is!
So:

1) What are you trying to do?
2) What are the error messages?  **This is important**.

---

### Post by Sethro on 2006-08-23
Okay so Iam using GTKPod to transfer music from my PC to the 4th Generation 20GB iPod.
Now I noticed that its read only. 

So I tried this command : cat /etc/mtab

Which gave me : 

/dev/hda1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw 0 0
/sys /sys sysfs rw 0 0
varrun /var/run tmpfs rw 0 0
varlock /var/lock tmpfs rw 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
devshm /dev/shm tmpfs rw 0 0
lrm /lib/modules/2.6.15-26-386/volatile tmpfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw 0 0
/dev/sdb2 /media/ipod vfat rw,nosuid,nodev,quiet,shortname=mixed,uid=1000,gid=1000,umask=077,iocharset=utf8 0 0
sethro@sethro-laptop:~$


Then I used this command : dosfsck /dev/sdb2 -a

Which gives me :

dosfsck 2.11, 12 Mar 2005, FAT32, LFN
Got 17498112 bytes instead of 19448812 at 16384

When I run GTKPod I get this error when reading the iPod

'/media/ipod/iPod_Control/iTunes/iTunesDB' does not exist. Import aborted.


HELP!

---

### Post by Sethro on 2006-08-23
> **Dubbayoo said:**
> once again wtf is ready only? complete sentences please, preferably english.

Dude take it easy.. Iam just trying to get help here.. sorry about the bad grammer.. lets move on..

---

### Post by RAOF on 2006-08-23
Ok.  
1) Can you write **anything** to the ipod?  Just try copying something to it with the file-browser.

2) Does the file /media/ipod/iPod_Control/iTunes/iTunesDB exist?

---

### Post by Sethro on 2006-08-23
Yes I can throw files on the ipod and delete then too but I just cant transfer music.

Also when I try to unmount the ipod i get the followiing error : 
umount: /mnt/ipod: device is busy
umount: /mnt/ipod: device is busy
eject: unmount of `/mnt/ipod' failed

---

### Post by Sethro on 2006-08-23
Oh yeah I checked and their is a file called 

/media/ipod/iPod_Control/iTunes/iTunesDB

Weird huh??

---

### Post by RAOF on 2006-08-23
Ok, so it would appear to be a GTKPod problem.  I've only ever played around with that for about 2 minutes.  How about trying some other iPod syncing program, such as Banshee?  That's in the repositories, and works for syncing my iPod.

Failing that, you could wait for someone who actually knows about GTKpod to come along :)

---

### Post by Sethro on 2006-08-24
Well guys ubuntu was fun and all. But I have decided to go back to using Windows XP, I just cant live without my iPod, and life just is not the same without Microsoft Office.. well it was a good run while it lasted :frown:

---

