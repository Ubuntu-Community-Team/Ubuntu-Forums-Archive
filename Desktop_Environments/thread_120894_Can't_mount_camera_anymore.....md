---
title: "Can't mount camera anymore...."
date: 2006-01-23
forum: Desktop Environments
---

### Post by encompass on 2006-01-23
I have now not been able to mount my camera or mp3play like I used too... I can mount my play manually... but can't see it in gnome at all... and with my camera I get this...
[[IMG]http://img58.imageshack.us/img58/6365/error1jm.th.png[/IMG]](http://img58.imageshack.us/my.php?image=error1jm.png)
any ideas?

---

### Post by cwaldbieser on 2006-01-23
[QUOTE=encompass]I have now not been able to mount my camera or mp3play like I used too... I can mount my play manually... but can't see it in gnome at all... and with my camera I get this...
[[IMG]http://img58.imageshack.us/img58/6365/error1jm.th.png[/IMG]](http://img58.imageshack.us/my.php?image=error1jm.png)
any ideas?[/QUOTE]
Does
```

$ gphoto2 --autodetect

```
find it?  What kind of camera is it?

---

### Post by encompass on 2006-01-24
If you take a quick look at the screen it shows the model of camera that I have... I ussually just got to the dir itself and find the files... I have never had success with gphoto it takes to much of my 200mb of ram ;p  But I will run the command when I get home and tell you the result none the less... and perhaps I can get the photos with out browsing... I use the driver, so to say.
Thanks for the help so far... in addition to my cam... I can use my mp3player that mounts the same way...

---

### Post by encompass on 2006-01-25
I really Don't think that one helped me...
If the Camera worked a week ago... wouldn't it work again without installed another program?

> jason@lappy:~$ gphoto2 --autodetect
ERROR: Bad option "--autodetect":
ERROR:     unknown option
gphoto2 2.1.6

Copyright (c) 2000-2004 Lutz Mueller and others

gphoto2 comes with NO WARRANTY, to the extent permitted by law. You may
redistribute copies of gphoto2 under the terms of the GNU General Public
License. For more information about these matters, see the files named COPYING.

This version of gphoto2 is using the following software versions and options:
gphoto2           2.1.6        gcc, no popt, exif, cdk, no aa, jpeg, readline
libgphoto2        2.1.6        gcc, EXIF, no ltdl, /proc/meminfo
libgphoto2_port   0.5.1        gcc, USB, serial without locking, no ltdl
Usage:
Short/long options (& argument)        Description
--------------------------------------------------------------------------------      --debug                          Turn on debugging


---

### Post by encompass on 2006-01-30
Actually, your right... after running it a few times it does have issues... it won't startup anymore.  Very insteresting... I have tried it on both my new and old computer and it does the same thing.:neutral:

---

### Post by cwaldbieser on 2006-01-31
[QUOTE=encompass]I really Don't think that one helped me...
If the Camera worked a week ago... wouldn't it work again without installed another program?[/QUOTE]
My bad, the correct option has a hyphen:
```

$ gphoto2 --auto-detect

```
If all other things are equal, you are right.  The camera should still work.  Because it is not working, that suggests that something in the equation changed.  Maybe a software update to the PC or to the camera? 

I get this for 
```

$ gphoto2 --list-cameras | grep ptio
	"Pentax Optio 33WR"
	"Pentax Optio 43WR"
	"Pentax Optio 450"

$ gphoto2 --version
gphoto2 2.1.6

Copyright (c) 2000-2004 Lutz Mueller and others

gphoto2 comes with NO WARRANTY, to the extent permitted by law. You may
redistribute copies of gphoto2 under the terms of the GNU General Public
License. For more information about these matters, see the files named COPYING.

This version of gphoto2 is using the following software versions and options:
gphoto2           2.1.6        gcc, no popt, exif, cdk, no aa, jpeg, readline
libgphoto2        2.1.6        gcc, EXIF, no ltdl, /proc/meminfo
libgphoto2_port   0.5.1        gcc, USB, serial without locking, no ltdl

```

---

### Post by encompass on 2006-01-31
I have some new information... I have a new computer... and I have been doing the same setup for this computer as I did for my old one...
And would you look at this... as soon as I install my webcam... I can't even mount my cd/dvd's and my camera doesn't even show up.... it was required to set my root pass for the webcam install and the driver.... and now it is not working.  Looks like that is the issue.

---

### Post by encompass on 2006-03-05
Yuppers... some how my user lost all rights and I restored them... and it works fine now.  Thanks for the help.\\:D/

---

