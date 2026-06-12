---
title: "root control"
date: 2009-05-21
forum: General Help
---

### Post by Relief on 2009-05-21
So i want to move a folder to "/usr/share/" but it seems I don't have permission. 

I get that you need root access, and that there is no root user. I have checked online to attempt to use or allow root access, but I guess I am not just getting it. I have tried using to sudo command and allowing root access but I guess I am not getting it. 

Can anyone help me figure out how to simply more a folder from my user documents to /usr/share/

or get a handle on this whole root deal. 

thanks

- Relief

---

### Post by lisati on 2009-05-21
Have you had a look [here]("https://help.ubuntu.com/community/RootSudo") yet?

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by spiderbatdad on 2009-05-21
a simple means is to launch your file browser as root:
```
gksu nautilus
```Then you can copy/paste, drag/drop whatever.
Linux uses permissions and ownerships on all files and directories.I find it easiest to view and edit these via command line using chmod and chown commands, but you can accomplish the same graphically under the properties permissions tab from the file browser by right clicking the file or directory.

---

### Post by niksa123 on 2009-05-21
By default there is always a root user in ubuntu but i don't know how u don't have one. Well try these commands and see what happens.

sudo passwd root  (this will ask you to enter a new passwd for root)

After setting a new root password use

su
Enter root passwd set above

and now use

mv <source path> /usr/share

---

### Post by lisati on 2009-05-21
Note: sudo and gksu don't really give you a root user. They *temporarily* give the current user "root privileges". (Double entendre not intended)

---

### Post by _Purple_ on 2009-05-21
```
sudo mv ~/Desktop/yourfolder /usr/share/

```

Replace ~/Desktop/yourfolder with your actual folder path. 

Please read this thread as well:
[http://ubuntuforums.org/showthread.php?t=716201](http://ubuntuforums.org/showthread.php?t=716201)

---

