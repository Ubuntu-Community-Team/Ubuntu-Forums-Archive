---
title: "write permission - only from terminal?!?"
date: 2006-01-10
forum: Desktop Environments
---

### Post by DRAGLYAR on 2006-01-10
Hello guys
I'm sorry for stupid question but I didn't find any topic regarding this - user priviliges:
I want to make my user have full read/write access to all drives and directories - and not by typing sudo commands all the time! How is this done?

---

### Post by brohan on 2006-01-10
sudo su

That gives you a root console.

---

### Post by DRAGLYAR on 2006-01-10
Eh sorry maybe I didn't say it right - I want all programs that I start from the menu to have write permission on all disks - just the user to have permanent write access to all disks - at least for the entire current session...

I've got a lot of files on the Fat32 partitions and if I cant work with them - whats the sence of it all?

Edit: Or if somebody tell me what to add to the launcher command of a program to start it as root or sudo I will appreciate that

---

### Post by brohan on 2006-01-10
If you sudo chmod -R 777 /path/to/your/fat32/partitions that makes all your fat32 paritions writeable.

I don't know how to add things to the menu, but I can tell you that you can use Applications > Tools > Run as different user to start nautilus (file manager) as root.

Or, if you want to make a nifty launcher, 'gksudo nautilus' will do ;)

Edit: gksudo anything will make anything run as root, if you want to play around with nifty launchers, that's the way.

---

### Post by DRAGLYAR on 2006-01-10
heh at least the gksudo add to a launcher works... That's good enough about now I think :D

---

### Post by lamego on 2006-01-10
[QUOTE=brohan]If you sudo chmod -R 777 /path/to/your/fat32/partitions that makes all your fat32 paritions writeable.

I don't know how to add things to the menu, but I can tell you that you can use Applications > Tools > Run as different user to start nautilus (file manager) as root.

Or, if you want to make a nifty launcher, 'gksudo nautilus' will do ;)

Edit: gksudo anything will make anything run as root, if you want to play around with nifty launchers, that's the way.[/QUOTE]

chmod will NOT work on FAT32 partitions because FAT32 do not support the unix permissions scheme.
If your problem is only related to those partitions you need to add umask=000 on your /etc/fstab options for those.
This will make them writeable for everyone.
Check [http://www.ubuntuguide.org/#automountfat](http://www.ubuntuguide.org/#automountfat) .

---

