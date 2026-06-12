---
title: "messed up Sansa Fuze usb drive"
date: 2009-04-11
forum: General Help
---

### Post by NFblaze on 2009-04-11
So..this morning I was attempting to move some music i converted into ogg format into my MP3 player which is Sansa FUZE... but somehow it kept saying this ''file system is read-only''.

Though, i also have a microSDHC card in there and its in the same file system format vfat. Plus, Im sure that I've moved music onto that internal memory before.

So anyhow, i figured oh this must be an error...so I looked up the properties thru gnome-gui and saw that under the volume tab that it could be edited for this volume...so i edited that only thing i changed was ''ro'' into ''rw''.  

It completely screwed the mounting abilities...so it wouldnt even open....so I navigated to /etc/mtab and edited something in there to say from ''rw'' int ''ro''.  

I also went into the Configuration editor and deleted a key.

So before i came to work today....the thing I've managed to get it at is for it to be mounted when I plug it in automatically...but it cant umount and gives me an error of saying ''this device is not in mtab it most likely mounted from the terminal''.... and when i use the df command at the terminal its not listed in there..

anybody ever come across a solution to this problem?
 thanks.

---

### Post by NFblaze on 2009-04-12
Nevermind I somehow fixed it....

very weird how that happened tho....


Thanks.

---

