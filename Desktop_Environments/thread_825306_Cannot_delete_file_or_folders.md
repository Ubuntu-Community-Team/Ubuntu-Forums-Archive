---
title: "Cannot delete file or folders"
date: 2008-06-10
forum: Desktop Environments
---

### Post by desktopdog on 2008-06-10
Hello. I have a folder and files that have a lock on them. When I try to delete them I get a message Can't change the permission or I don't have permission to delete file or folder. I tried using chmod to change permissions but no good.

Can any one help please?

---

### Post by lswb on 2008-06-10
Could you show the output of ls -l on the folder you're referring to?

---

### Post by Victormd on 2008-06-10
> **desktopdog said:**
> Hello. I have a folder and files that have a lock on them. When I try to delete them I get a message Can't change the permission or I don't have permission to delete file or folder. I tried using chmod to change permissions but no good.

Can any one help please?

you will have to open the terminal and use "sudo rm" command but be very careful!!!!

usage:
```
sudo rm -r FOLDERNAME
```
if you do not include the folder name, this command can wipe your entire HD so be careful...
I know this may seem extreme but it's not, and don't be frightened by it, it's a normal command, but can do a lot of damage if not used properly... so, again, don't forget to replace FOLDERNAME with the name of the folder you wish to remove...

If you're not familiar with the terminal usage, come back so we can further assist you...

---

