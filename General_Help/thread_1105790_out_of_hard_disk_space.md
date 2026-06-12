---
title: "out of hard disk space"
date: 2009-03-25
forum: General Help
---

### Post by Sayadina on 2009-03-25
I have an eee-pc 901... Installed ubuntu 8.04 on it, but made a fatal mistake, by installing the operating system on hte 4-giga hard-disk... Now my litle eee-pc no longer has free space for anything on that hard... not even updates can't be installed


From what i have figured out on my own i would need to move the /home folder and the /etc folder to make some nice space, on the other hard-disk. I know that unlike windows, on linux it is possible, but do not know how to do it... 


i am a complete noob on linux... and do not have the silghtest idea how to do this without having to search a portable cd-rom to reinstall everything again. 


p.s. on the other partition the /HOME from the old operating system has remained. and the partition is ext3, and the data on it is no longer important to me.... but the space is :D



Please help a noob... 


thank you,
Lots Love Saydina

---

### Post by mikeize on 2009-03-25
Basically, you just need to copy your /home folder to wherever you want it to be, and then make sure Ubuntu knows where to find it.  You can change where Ubuntu looks for /home in your /etc/fstab file.

Be very careful editing this file (make a backup, and know how to restore it from terminal)... but essentially, you will make an entry like the others, where you designate the appropriate volume as the place to mount /home.  

You can find the device ID by right-clicking on it and selecting properties>volume.

*just replace your old leftover unneeded /Home with the one you want to move, and then edit your fstab as I told you above (read up on fstab a bit first though! :D )

---

### Post by Sayadina on 2009-03-25
Okey... my main problem isn't about the home/ partition but about what else i could move from the filesystem so everything i install from now on (incuding updates) will not go on the small hard drive but on the big one... :|

---

