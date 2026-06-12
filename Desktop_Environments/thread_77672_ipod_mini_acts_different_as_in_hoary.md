---
title: "ipod mini acts different as in hoary"
date: 2005-10-17
forum: Desktop Environments
---

### Post by anatole on 2005-10-17
hi, 
after i installed breezy i wanted to set up my ipod as it was in breezy... my way to get it working was this howto: [http://www.ubuntuforums.org/showthread.php?t=36632&highlight=ipod](http://www.ubuntuforums.org/showthread.php?t=36632&highlight=ipod) earlier, except for adding the line for the ipod in fstab (i didn't have to add anything). it worked in hoary, but not in breezy: my ipod mounts, but i cannot eject it properly - in fact, ejecting is really strange. (i tried adding the line in fstab, and effects were the same even after a restart.) what happens is:
attila@nanaki:~$ eject ipod
eject: unable to eject, last error: Invalid argument

but, it ejects anyway, because the iPod disappears from the "Places" list and it is not accessible anymore for GtkPod, but tha ipod still says "do not disconnect" .
after that, i tried:
attila@nanaki:~$ sudo eject /media/ipod
and it worked. no errormessages, no "do not disconnect" signs. the strange thing is, ejecting does not require superuser privileges when automounted.. am i wrong? it works with cd-roms, and in fact, when ejecting ipod, my breezy does not complain about being a root or not, and it does try to eject the ipod, but not in a proper way. anyone know the cause of this and/or how to fix it?

---

### Post by the_purulent on 2005-10-17
I have a mini and I had to reference it's mount point directly to make it unmount (and even then it takes a few minutes to happen).

sudo eject /dev/sda2 (which was where mine was mounted.)

---

### Post by anatole on 2005-10-17
[QUOTE=the_purulent]I have a mini and I had to reference it's mount point directly to make it unmount (and even then it takes a few minutes to happen).

sudo eject /dev/sda2 (which was where mine was mounted.)[/QUOTE]

it works for me with sudo, (even sudo eject /media/ipod), the funny thing is, that in hoary i didn't need sudoing and now it's quite a bother.

---

