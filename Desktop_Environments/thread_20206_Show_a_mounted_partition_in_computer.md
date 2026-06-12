---
title: "Show a mounted partition in computer:/// ?"
date: 2005-03-15
forum: Desktop Environments
---

### Post by Julius on 2005-03-15
I have mounted my Windows partition on /media/windows, and it's set to automatically mount when the system starts.
However, it doesn't show in "Computer:///"
I'm using Hoary preview, and I remember it showed in Warty without any problems... but I think the mounted location was different  in warty, not sure of that though.

Any suggestions on how to make it appear ?

Thanks in advance

---

### Post by Julius on 2005-03-17
It seems it was some kind of bug, because I have updated 150 packages and now it's shown.

This thread can be closed :P

---

### Post by Julius on 2005-03-19
:(
After restarting my windows partition was gone again. It came back for a while after I run the updates, but it again dissapeared after restarting.

What am I doing wrong?

---

### Post by bored2k on 2005-03-19
[QUOTE=Julius]:(
After restarting my windows partition was gone again. It came back for a while after I run the updates, but it again dissapeared after restarting.

What am I doing wrong?[/QUOTE]
 Hoary Preview version. Stuff will pop out.
If you have everything like [http://ubuntuguide.org/#mountunmountntfs](http://ubuntuguide.org/#mountunmountntfs) and the things below, its not you, its Ubuntu.

If its annoying you can just add a bookmark to media/windows :) .

---

### Post by Julius on 2005-03-19
Yeah I've done it the right way... I have the same exact line in /etc/fstab
Well I guess I'll have to wait until the bug gets fixed. Is it in bugzilla already?

---

### Post by Buffalo Soldier on 2005-03-19
[QUOTE=Julius]Yeah I've done it the right way... I have the same exact line in /etc/fstab
Well I guess I'll have to wait until the bug gets fixed. Is it in bugzilla already?[/QUOTE]
 You've posted in the Warty section of the forum :)

I had the same problem. Somewhere in the forum I read a suggestion to add **user** to the line in fstab. Original:```
/dev/hda1      /media/windows 	vfat    umask=000       0       0
```
New:```
/dev/hda1      /media/windows 	vfat    **user**,umask=000       0       0
```

---

### Post by Davepet on 2005-03-20
>> You've posted in the Warty section of the forum

This post was started before the forum reorginization, near as I can tell.

Dave

---

### Post by telmo on 2005-03-20
[QUOTE=Buffalo Soldier]You've posted in the Warty section of the forum :)

I had the same problem. Somewhere in the forum I read a suggestion to add **user** to the line in fstab. Original:```
/dev/hda1      /media/windows 	vfat    umask=000       0       0
```
New:```
/dev/hda1      /media/windows 	vfat    **user**,umask=000       0       0
```[/QUOTE]

Is it possible to rename the partitions in Computer:/// ?

thx

---

