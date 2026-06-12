---
title: "Help computer wont boot, need data"
date: 2007-10-10
forum: Desktop Environments
---

### Post by trojanlinux on 2007-10-10
When i woke up my computer was frozen, I tried to restart it and not it wont boot.  I have data on the HD that I need.  I dont have a CDrom drive.  It starts in the disk check then does a bunch of stuff , buffer I/O error on dedive sda1, loical block, exception Emaskect (to much to type) then it says

an automatic file system check of the rool filesystem failed...
the progtam apt-get is not installed you can install it by typing apt-get install get

i type that in the command prompt root and it repeats the same message

---

### Post by scrooge_74 on 2007-10-10
You could be experiencing HD failure if you can enter into Grub try the safe mode see if you can log in as root.

It would be a good idea to take the disk out and put it in a computer with a CDROM so you can boot a live CD and make a backup of your data

---

### Post by trojanlinux on 2007-10-10
its gives me a root prompt, how do i log into safe mode? 

and how do i take the HD out of a laptop?

---

### Post by scrooge_74 on 2007-10-11
if you get a root prompt you are log in as root.

If you dont know much about hardware then I suggest you talk to someone close to you that knows. Each brand of laptop has his own idea on how to get to the HD bay.

---

### Post by perlluver on 2007-10-11
Type in fsck, and let it run.  It will complain about all the bad I/O's just let it.  When it is done type login at the root prompt, and login and type startx.  I kinda had the same problem and that seemed to work for me.

---

