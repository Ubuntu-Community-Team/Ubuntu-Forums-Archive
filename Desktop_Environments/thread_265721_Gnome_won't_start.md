---
title: "Gnome won't start"
date: 2006-09-26
forum: Desktop Environments
---

### Post by dipswitch on 2006-09-26
I guess I've had enough. PC was running fine on Friday but when I came in to work today Gnome will not start at all. I've no idea what the problem is and I just don't have the time to mess around with this anymore. Here is the screen I boot to. :( 

[IMG]http://img157.imageshack.us/img157/8467/donewithlinuxja4.jpg[/IMG]

So is there an easy way to whipe out my linux partitions and add to my XP NTFS partition? Or is it just going to be easier to whipe the drive clean.

---

### Post by pay on 2006-09-26
You can wipe a parition in Windows using Start --> Control Panel --> Administrative Tools --> computer Management --> Disk Management
Then you can delete the paritions you don't want (Right click Delete logical drive) and format a new parition. Then put in you windows cd and boot into the recovery console. Type fixboot and fixmbr (or maybe fix boot, fix mbr i can't remember) to get rid of grub.

---

