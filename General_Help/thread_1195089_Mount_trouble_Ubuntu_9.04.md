---
title: "Mount trouble Ubuntu 9.04"
date: 2009-06-23
forum: General Help
---

### Post by hhoyt on 2009-06-23
I'm fairly new to Linux and am having trouble with mounting my windows drives.

Several hours into fstab I (seem) to have them mounted but I suppose I really still do not understand the concept of mount:

If I MOUNT /dev/sdc7 /mnt/Hdrive (or put in fstab)

the terminal MOUNT shows
/dev/sdc7 on /media/Hdrive type vfat (rw)

That seems what I want. 
Problem being I must be root or su to really write to the disk ???

This produces the problem that using Kompozer to change html, I want PUBLISH to write the results
back to my html source repository on the h drive. 
But I get a 550 authorization error. Even if, from terminal, I 
SUDO KOMPOZER I fail, tho I can SAVE AS and it then writes to the drive.

I suspect I am mounting ok and that Kompozer is not handling the write but, frankly, the authority levels in linux leave me with a migraine. 
Can someone help advise what I am doing wrong ?

Thanks !

Howard

---

### Post by hhoyt on 2010-08-30
Honestly do not recall the solution. Perhaps I needed to run Kompozer as root, but no problems now.

Tks, Howard

---

