---
title: "Root: Permission Denied"
date: 2009-05-30
forum: General Help
---

### Post by ganny on 2009-05-30
Hi all! I'm ashamed to say my first post here is a plea for help, please forgive me :KS

My problem is that I have a network drive which I have always mounted and used as my storage for Documents etc so that I can access it anywhere. Today I reinstalled Ubuntu, and hence had to remount my network drive, which I did by adding the following line in /etc/fstab:[INDENT]```
//share  /media/share  cifs rw,user,exec 0 0
```[/INDENT]The share mounts perfectly except for the small problem that when I go to access files, nearly half the files have permissions on them which make it impossible to modify or even read them. So I thought I'll just use root to sort this out, and when I go to the terminal and try a chmod, it hit me up with a "Permission Denied" error for all those files. I checked the owner of the files, and its some random uid: #35000!!

I have no idea what to do now: the supergod that was root has failed me, so any guidance would be greatly appreciated!

---

