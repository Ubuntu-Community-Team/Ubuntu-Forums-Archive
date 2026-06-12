---
title: "Changing Folder Permissions"
date: 2006-09-21
forum: Desktop Environments
---

### Post by Quickdood on 2006-09-21
I have a folder called /osshare.  For some reason it is set up so only the administrator can modify it. I want to change the permissions so the user Quickdood can modify any thing in the folder and put new files in that folder.  How can I modify the permissions of this folder.  Thanks!!!

---

### Post by Jussi Kukkonen on 2006-09-21
Look at the ownership and read/write access information of the directory in nautilus, or do a *ls -ld /path/to/osshare*.

If the directory owned by someone else, then change that first:
```
sudo chown quickdood:quickdood /path/to/osshare
```
If you still have no write access, change the permissions:
```
sudo chmod u+w /path/to/osshare
```
more info: *man chown*, *man chmod* 

(all of this is no doubt possible in nautilus too)

---

### Post by crane on 2006-09-21
> **Jussi Kukkonen said:**
> 
(all of this is no doubt possible in nautilus too)

 Yes if you are not familiar with the terminal commands and want to use GUI, you can do so.
First you have to open a nautilus window with root access.
```
sudo nautilus
```
This will open a nautilus session with root priviledges. Now, just navigate to the folder you want to modify. Right click on the folder> click permissions tab. Then set how ever you need.

Good luck!

---

