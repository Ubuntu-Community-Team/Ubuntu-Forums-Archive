---
title: "How do i install UT2004 (ECE) on Ubuntu?"
date: 2006-10-07
forum: Gaming &amp; Leisure
---

### Post by coolbian57 on 2006-10-07
How do I install Unreal Tournament 2004 onto Ubuntu?  Once I have inserted my disc i click on install.sh, but it doesn't do anything.  I tried opening install.exe with WINE, but that did not work either.

Can anyone help me with this issue?

Also, i don't know which diectory to save it in.  I will probably just put it in my media or bin but i don't know if this will work or not.

---

### Post by haxer on 2006-10-07
type in sh in terminal then drag and drop the linux installer into terminal first su then password then sh drag and drop and then enter look at my a couple a sides down and youll find out

---

### Post by coolbian57 on 2006-10-07
```
sh: /media/cdrom/linux-installer.sh: /bin/sh: bad interpreter: Permission denied
```

This is excactly what it sais when i do that.

---

### Post by coolbian57 on 2006-10-07
Okay I figured everything out, i just have one last step!

I have the UT2004 patch and i need to move it into the UT2004 files...

But when i select copy/paste, or when i try to drag and drop the files, it sais that i do not have permissions to write to the folder (ut2004)

So essentially i guess that i don't have privelages to do that...

---

### Post by CAUSTICROUTER on 2006-10-07
Try changing the permissions of the ut2004 by right clicking, then going to properties, then permissions, and check off the write permission.

---

### Post by Ayman on 2006-10-07
Type the following in a terminal:
```
$ sudo nautilus
```
A file manager with root permissions will open, now copy the files around.

Hope this helps.

---

### Post by haxer on 2006-10-07
or gksudo nautilus i use this

---

### Post by jdunn on 2006-10-08
This should answer most of your questions:

[http://www.thehaus.net/Tips/UT/ut2004icculusfaq.shtml]("http://www.thehaus.net/Tips/UT/ut2004icculusfaq.shtml")

---

### Post by Perfect Storm on 2006-10-09
```
sudo sh /media/cdrom/linux-installer.sh
```

Go with the default settings. Exit the installer (don't hit the start button, you just end up with permission problems).

Grab the megapack here: [http://www.3dgamers.com/dlselect/games/unrealtourn2k4/Missions/ut2004megapack-linux.tar.bz2.html](http://www.3dgamers.com/dlselect/games/unrealtourn2k4/Missions/ut2004megapack-linux.tar.bz2.html)
save it to your Desktop.

```
cd && cd Desktop
tar jxvf ut2004megapack-linux.tar.bz2
cd ut2004megapack-linux
sudo cp -r * /usr/local/games/ut2004
```

Done.

---

