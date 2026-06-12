---
title: "All almost worke now :D but"
date: 2006-07-19
forum: Desktop Environments
---

### Post by doomstone on 2006-07-19
Hello, i just started out on ubuntu last night. and let me say, this os must have been mabe by gods :D

I have almost all nailed down now but from 4 small problems

1: I have just gotten WoW to run smoot with wine, but i can't use my mouse bottom 4 and 5.
EDIT: (My mouse is "Microsoft Wireless Laser Mouse 6000")

2: My mouse is lagging a bit, is there a way i can run hardware mouse or something like that there will remove the lag?

3: How can i download Video codes so can i view my videos?

4: I have a 300gb sata hd with a NTFS partition on? how can i reformate it so it is in ext3 and points to /home/doomstone/Media 2/ ?

---------------------------
Well that is the only problems i have encounterd so far, that i'm not able to fix myself.

Finaly do you guys know a god music program for linux there look/worke like Itunes?

Thanks Kasper

---

### Post by reacocard on 2006-07-19
1) Change the part of your /etc/X11/xorg.conf that corresponds to your mouse to look like this:
```
Section "InputDevice"
	Identifier	"Logitech USB Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option          "Buttons"               "7"
	Option          "ButtonMapping"         "1 2 3 6 7"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"false"
EndSection
```
if your Identifier line is different, don't change it.

2) System -> Preferences -> Mouse
3) [https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)
4) use gparted to reformat. then you'll need to edit your /etc/fstab to mount it.

take a look at rhythmbox, the interface is almost exactly like itunes.

---

### Post by goobers on 2006-07-19
I prefer AmaroK as a music player. The latest version (1.4) is the best music player for linux IMO

---

### Post by reacocard on 2006-07-19
```
I prefer AmaroK as a music player. The latest version (1.4) is the best music player for linux IMO
```
actually, i use Exaile myself. but rhythmbox is the closest to itunes.

---

### Post by doomstone on 2006-07-19
> **reacocard said:**
> ]
4) use gparted to reformat. then you'll need to edit your /etc/fstab to mount it.

I have now formated now. but i can't figer out what to edit in /etc/fstab

---

### Post by reacocard on 2006-07-19
here's an example for the line to add:
```
/dev/hdb1 /media/extra ext3 defaults 0 0
```
replace /dev/hdb1 with the appropriate device for that harddrive (gparted will tell you.)
replace /media/extra with the place you want to mount it to.

---

### Post by doomstone on 2006-07-19
> **reacocard said:**
> 2) System -> Preferences -> Mouse can not find anything there there would make my mouse stop lagging

Else do anything worke now

---

