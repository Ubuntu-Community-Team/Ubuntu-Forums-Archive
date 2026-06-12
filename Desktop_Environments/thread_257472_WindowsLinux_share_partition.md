---
title: "Windows/Linux share partition"
date: 2006-09-14
forum: Desktop Environments
---

### Post by Uncle Spellbinder on 2006-09-14
I've created a fat32 partition in which I wanted to share stuff between Windows and Ubuntu. Apparently that's not the way to go as I've read in a search and I get this:
```

error: device /dev/sda4 is not removable

error: could not execute pmount
```

How can I share. I have no problem reformatting the partition if necessary. I just want a partition that is accessible from Windows and Ubuntu. Possible? How?

---

### Post by aysiu on 2006-09-14
Paste these commands in the terminal: ```
sudo mkdir /shared
sudo umount /dev/sda4
sudo nano -B /etc/fstab
``` If there's a line for /dev/sda4, delete it (Control-K).

Then, add this line ```
/dev/sda4 /shared vfat iocharset=utf8,umask=000 0 0
``` Save (Control-X, Y, Enter). ```
sudo mount -a
``` Then go to /shared, and you should see your shared partition.

---

### Post by Uncle Spellbinder on 2006-09-14
@ aysiu

Thank you so much!  Worked like a charm.

---

### Post by aysiu on 2006-09-14
Great to hear.

If you want it to show up as a desktop icon, just paste in this command: ```
ln -s /shared ~/Desktop/shared
``` There's another way to mount it so that it automatically appears on the desktop without the *ln* command--you can mount it to the /media folder--but I've seen a few cases where mounting FAT32 inside /media brings up weird problems (locks on some folders but not others).

---

### Post by Uncle Spellbinder on 2006-10-01
> **aysiu said:**
> Great to hear.

If you want it to show up as a desktop icon, just paste in this command: ```
ln -s /shared ~/Desktop/shared
```

How can I undo this? I would prefer not to have the Icon on the desktop.

---

### Post by Uncle Spellbinder on 2006-10-01
Anybody?

---

### Post by Uncle Spellbinder on 2006-10-01
One more time before getting ready for work....

Ideas, anyone??

---

### Post by aysiu on 2006-10-01
> **Uncle Spellbinder said:**
> How can I undo this? I would prefer not to have the Icon on the desktop.
```
rm ~/Desktop/shared
```

---

### Post by Uncle Spellbinder on 2006-10-01
> **aysiu said:**
> ```
rm ~/Desktop/shared
```

Thanks, aysiu. I knew you'd show up sooner or later. ;)

I don't know why I could not remember something so simple. :oops:

---

### Post by lmaranhao on 2006-10-22
Hello guys.

After I install ubuntu my windows stopped seeing a partition. 

I want to set this partition in a way windows can see it without formating it. 

Does this commands work for this problem?:confused: :confused: 

> Paste these commands in the terminal:
Code:

sudo mkdir /shared sudo umount /dev/sda4 sudo nano -B /etc/fstab

If there's a line for /dev/sda4, delete it (Control-K).

Then, add this line
Code:

/dev/sda4 /shared vfat iocharset=utf8,umask=000 0 0

Save (Control-X, Y, Enter).
Code:

sudo mount -a

Then go to /shared, and you should see your shared partition.

Thanks

---

### Post by dracomordag on 2007-02-13
will those command codes create a partition from scratch?

 to install ubuntu on an XP machine, i originally partitioned the 75 GB drive 75% Windows and 25% Ubuntu. now that i've got Ubuntu up and running pretty well, i'd like to start moving all my files over from Windows.

how can i change split windows into a partition of 50% windows, 25% share? (I need to keep windows at at least 50% due to the amount of files i have on the drive)


would it be easiest to make the partition and move the files onto it in windows, then come back to ubuntu and access the shared partition, etc.?

---

### Post by dracomordag on 2007-02-13
hmm?

---

### Post by Fahuadai on 2007-02-13
The way i have partitioned my laptop is that i installed windows with a 20GB partition, The installed kubuntu onto a 10BGB partition. finally i formatted a partition in ext3 (with the ubuntu live cd). I then set this to be my /home folder.  Subsequently i then booted into windows and used [_this_]("http://www.fs-driver.org") program to access the shared partition.

 It works fine with both ubuntu and windows sharing the same documents.  The only problem i have is if i set the laptop to hibernate then boot windows, it can not access the drive then until ubuntu is shut down.  

Otherwise it works perfectly allowing me full access without duplication. 

more info from this _[thread]("http://www.ubuntuforums.org/showthread.php?t=357883&highlight=share+linux+windows+partition")_

You should be able to resize partitions from inside ubuntu, but i'm not sure how.

---

