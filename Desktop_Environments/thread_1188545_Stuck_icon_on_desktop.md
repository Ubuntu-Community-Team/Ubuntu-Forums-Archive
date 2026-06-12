---
title: "Stuck icon on desktop"
date: 2009-06-15
forum: Desktop Environments
---

### Post by cyberjohn on 2009-06-15
while working on samba networking issues in 9.04, an icon named "my documents on john.volume" appeared on my desk top.  I cannot now be removed, renamed, deleted, moved.  It is there after reboots. 

It does not however show when the contents of the Desktop directory are listed

Help!!!!!

---

### Post by scrooge_74 on 2009-06-15
Did you try umounting it?

---

### Post by cyberjohn on 2009-06-15
I have not been able to find a way to do that.

---

### Post by scrooge_74 on 2009-06-15
Right click on it and click on unmount drive, or from a terminal sudo umount /address of drive

---

### Post by cyberjohn on 2009-06-15
first off, there is no unmount option when I right click on the icon.  It doesnot look like a mounted drive.  it looks like a text document of some sort. 
secondly trying to unmount it  from the CLI gives me a file not found.

I tried doing```
 ls  -la Desktop
```
and got the following result:
```
johnp@toshlaptop:~$ sudo ls -la Desktop
total 16
drwxr-xr-x  2 johnp johnp 4096 2009-06-15 17:40 .
drwxr-xr-x 43 johnp johnp 4096 2009-06-15 18:57 ..
-rw-r--r--  1 johnp johnp  187 2009-06-10 12:21 Howto: Fix Windows share browsing issues - Ubuntu Forums.desktop
-rw-r--r--  1 johnp johnp  189 2009-06-15 17:40 [ubuntu] Stuck icon on desktop - Ubuntu Forums.desktop
```

---

### Post by days_of_ruin on 2009-06-16
See if my post in this thread is any help: [http://ubuntuforums.org/showthread.php?t=1187988]("http://ubuntuforums.org/showthread.php?t=1187988")

---

### Post by cyberjohn on 2009-06-16
thanks, I had noticed your post, but it doesnt apply....   this icon is not related to anything that is actually mounted.  It looks like it may have been at sometime, but it persists even if the network is totally disconnected.  So  I dont see how your suggestion would be of help
Thx tho

---

