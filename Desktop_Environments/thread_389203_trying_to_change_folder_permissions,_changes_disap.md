---
title: "trying to change folder permissions, changes disappear!"
date: 2007-03-20
forum: Desktop Environments
---

### Post by rudeboymcc on 2007-03-20
Hi. I've got ubuntu and have a hard disk (fat32) connected by sata through a pci sata adator. 

I can read the drive fine and write to it fine. 

Now i need to set permissions for a folder on the drive, so that anyone can read it (for my samba share). 

so i used 
sudo nautilus

went tot he folder's properties, and tried to tick the read tick box under "others". As soon as i tick it, the tick appears and then disappears. any changes i make that aren't for the owner (which is my user) are changd back. 

I've tried chmod 644 /media/MOVIES/Movies. again tehre are no errors but also no changes made. 

can any one help me?

---

### Post by hardyn on 2007-03-20
.

---

### Post by rudeboymcc on 2007-03-20
Soryr don't know why your post is only showing up as a full stop. here's what you said:
***************
Fat32 is not a permissions aware file system.

are you having trouble getting other people to read the drive? or just trying to
set things up right now?
***************

I can read the drive fine, and now I need to allow anyone (as in the nobody account) to read it as well. 

As for fat32 not being aware of permissions, i don't understand this. I have just set a folder on the same drive to only be accessbile by me. If you go through windows and try to open it then it will ask for my username and password. and if it wasn't aware of permissions, then surely it would allow anyone to read it? 

Someone has just told me it may be the way I am mounting the drive. does anyoen have a line for fstab to mount vfat drives?

---

