---
title: "Deleting read only directories and files on SD card"
date: 2009-04-04
forum: General Help
---

### Post by Matt 6:27 on 2009-04-04
I just deleted a number of files and directories from an SD card (or so I thought) in order to make room for new material. When I unmounted the SD card, it asked if it could empty the trash, to which I said ok. Unfortunately, the system created a .Trash directory on the SD card containing all the deleted directories & files.  Now I'm stuck with a 1GB SD card that only has 600+MB of available space.  I've tried removing using rm, rm -Rf and a basic delete from nautilus, but in all instances the system won't remove/delete because the .Trash directory and all subdirectories and files are "Read Only".  This is the result whether I'm running as root or as the usr with ownership privileges.  I also attempted to change permissions (again via Nautilus and also with chmod) but it won't let me do so.  Anyone out there know how I can blow these deleted files off my SD card?  Thanks in advance!!!

---

### Post by ShaunG on 2009-04-04
Open a terminal and cd into the mount point of the sd card. It's probably something like /media/disk

Then run chmod -R 777 on whichever directory you want to delete.

Then run rm -rf on that directory.

I think that will work.

---

### Post by Matt 6:27 on 2009-04-04
I tried that, but gave it another go and got the same result...

"rm: cannot remove `.Trash-1000/files/What I want to be.pwi': Read-only file system"

Any other ideas are welcomed.

Is there any way to reformat a disk like I used to do under that other OS?

---

### Post by ShaunG on 2009-04-04
You can use gparted

```
sudo apt-get install gparted
```

You'll then find it in System -> Places -> Administration under the heading Partition Editor.

---

### Post by Matt 6:27 on 2009-04-04
At first it took me a few minutes to figure out how to get GParted to work (hint: first unmount the media using GParted, then reformat), but that did the trick!

Thanks so much!

---

### Post by ShaunG on 2009-04-04
No problem :)

---

