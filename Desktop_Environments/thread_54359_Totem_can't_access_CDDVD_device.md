---
title: "Totem can't access CD/DVD device"
date: 2005-08-04
forum: Desktop Environments
---

### Post by snafoo on 2005-08-04
Hi,

I get an error when selecting 'Play CD/DVD...' from the Totem menu. ('Failed to play Audio/Video Disc - Failed to open device /dev/hdb for reading: Permission denied'.) A DVD is mounted already and I can access it with Nautilus. The mount point for the drive is /media/cdrom0. A group named 'cdrom' exists and I am a member of that group.

Does anyone have an idea, why Totem isn't able to access the drive?
Thanks in advance!

---

### Post by heimo on 2005-08-04
Have you seen this?
[http://www.ubuntuguide.org/#dvdplayback](http://www.ubuntuguide.org/#dvdplayback)

---

### Post by snafoo on 2005-08-04
Yes, I read that, so 'libdvdcss2' is installed.

When selecting a single VOB file Totem manages to play it. It goes just fine. But playing a DVD from the menu isn't possible. The mentioned error always shows up.

---

### Post by ssck on 2005-08-04
i get the error of no plug ins.but i have installed all the required files mentioned in the guide.what else do i need to do ?

---

### Post by heimo on 2005-08-04
I have a symlink:
 ```
lrwxrwxrwx  1 root root 3 2005-08-04 06:22 /dev/dvd -> hda
``` 

to this device:
 ```
brw-rw----  1 root floppy 3, 0 2005-08-04 06:22 /dev/hda
``` 

which has a line like this in /etc/fstab:
```
/dev/hda	    /media/cdrom0   udf,iso9660 ro,user,noauto  0	   0
``` 

When I insert a dvd in that drive, it gets automounted, totem starts and playback begins. My user is in floppy group. Is your setup similar?

---

### Post by ssck on 2005-08-04
[QUOTE=heimo]I have a symlink:
 ```
lrwxrwxrwx  1 root root 3 2005-08-04 06:22 /dev/dvd -> hda
``` 

to this device:
 ```
brw-rw----  1 root floppy 3, 0 2005-08-04 06:22 /dev/hda
``` 

which has a line like this in /etc/fstab:
```
/dev/hda	    /media/cdrom0   udf,iso9660 ro,user,noauto  0	   0
``` 

When I insert a dvd in that drive, it gets automounted, totem starts and playback begins. My user is in floppy group. Is your setup similar?[/QUOTE]

hi thanks for looking into this.i have these settings :-

lrwxrwxrwx  1 root root           3 2005-08-05 08:22 cdrom -> hdc
lrwxrwxrwx  1 root root           3 2005-08-05 08:22 cdrw -> hdc

lrwxrwxrwx  1 root root           3 2005-08-05 08:22 dvd -> hdc

in the fstab i have this :-

/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0

is it OK ? 

thanks

---

### Post by professor_chaos on 2005-08-04
Are these pressed DVD's or homegrown?

I was getting the same symptoms when burning dvds, until I figured out how to do it properly.

---

### Post by ssck on 2005-08-04
[QUOTE=professor_chaos]Are these pressed DVD's or homegrown?

I was getting the same symptoms when burning dvds, until I figured out how to do it properly.[/QUOTE]

pressed dvd's.

---

### Post by heimo on 2005-08-04
[QUOTE=ssck]
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0

is it OK ? 
[/QUOTE]

All those look fine. But what permissions do you have on device /dev/hdc?
 ```
ls -l /dev/hdc
``` 
And is your user in that group?
 ```
groups
```

---

### Post by ssck on 2005-08-05
[QUOTE=heimo]All those look fine. But what permissions do you have on device /dev/hdc?
 ```
ls -l /dev/hdc
``` 
And is your user in that group?
 ```
groups
```[/QUOTE]

hi,

these are my settings :-

$ ls -l /dev/hdc
brw-rw----  1 root cdrom 22, 0 2005-08-05 16:09 /dev/hdc
$ groups
nameless adm dialout cdrom floppy audio dip video plugdev lpadmin scanner admin


yes, it looks like i am in the group

---

### Post by heimo on 2005-08-05
And do you need to mount the disk manually (clicking on some menu or using mount command)? Can you find out which version of kernel and the exact version of the package ... I think it's possible in synaptic.

And does it behave the same way if you do or do not mount the dvd before trying to play it in totem? Could you try other programs, like gxine and vlc?

---

### Post by ssck on 2005-08-05
[QUOTE=heimo]And do you need to mount the disk manually (clicking on some menu or using mount command)? Can you find out which version of kernel and the exact version of the package ... I think it's possible in synaptic.

And does it behave the same way if you do or do not mount the dvd before trying to play it in totem? Could you try other programs, like gxine and vlc?[/QUOTE]

this is the version from synaptic :-

1.1.1-0ubuntu3~5.04ubp1

i have tried gxine, vlc, ogle.all of it can play the dvd with varying degree of success.the best response is ogle.however, after playing for about 10 mins, it will just freeze up.i am not sure why.there is also another thread on the description of the problem :-

[http://www.ubuntuforums.org/showthread.php?t=54248](http://www.ubuntuforums.org/showthread.php?t=54248)

any help will be very much appreciated.

thanks. ](*,)

---

