---
title: "changing permissions of folders?"
date: 2004-12-21
forum: Desktop Environments
---

### Post by puzzledm on 2004-12-21
Hello - when you copy something from a cd it immediately becomes locked by root (or read only or something)

I know how to right click and go to properties and change permissions but how do I make those changes affect everything in that folder and any folders in that folder and so on.

It takes ages to open each folder, select all, right click, properties change permissions and then open the next folder within their and select all, right click .... and so on and so forth ....

Please help.

---

### Post by haha on 2004-12-21
how about changing your account TO root?

$ su -

# cp /mnt/cdrom/dir/ /to/mydir/dir/

---

### Post by astoltz on 2004-12-21
Some things are much easier from the command line.  The command to change "permissions" (also known as the mode) is chmod.  type "man chmod" at your terminal and you can read up on the details.  After you copy the files, I suspect what you want is ```
sudo chmod 755 -R /to/mydir/dir/
``` The "-R" switch tells chmod to work on all files and sub-directories in /to/mydir/dir/.  The above will give only the files' owner read/write/execute permission so you probably want to make yourself the owner also (as opposed to the owner being root) ```
sudo chown userid:userid  -R /to/mydir/dir/
```  I suppose you could set the read/write/execute permission for everyone (chmod 777) and skip the chown part but that may present some security concerns.

---

### Post by puzzledm on 2004-12-21
very good worked well ... thank you for your quick response

is there any way of doing it through nauilus ?

---

### Post by astoltz on 2004-12-21
[QUOTE=puzzledm]very good worked well ... thank you for your quick response

is there any way of doing it through nauilus ?[/QUOTE]
 you can open nautilus as root by typing "sudo nautilus" at the teminal.  Then you can change permissions of directories and groups of files, but I don't know how to make nautilus do the recursive trick (work down through any sub-directoies and files).  Be careful working as root in nautilus though, as the permissions that would normally prevent you from moving or deleting critical system files won't stop you as root.

---

