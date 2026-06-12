---
title: "Problem with wow installation progress..."
date: 2006-01-26
forum: Gaming &amp; Leisure
---

### Post by Sordo on 2006-01-26
I got wine installed and started to install world of warcraft, but problem occured when the installer wanted me to change disk2 on the drive. But accidentally I can't get my drive opened. 
I try to umount and use sudo umount /media/cdrom0/ -l
but still i can't get it open.
Help please!

---

### Post by kidcharles on 2006-01-26
When you tried to umount did it say that the device is busy?

If you have room, you might try to just copy all of the contents of the CDs onto your hard drive and install from the drive. I haven't tried this myself.

---

### Post by Sordo on 2006-01-27
I solved the problem..
I moved all 4 Installer Tome *.mpq files from 4 cd:s and confed wine driver information with winecfg and confed it so that it used the folder where .mpq files were.
In that way installer didn't ask to change disks and now wow works fine.

---

### Post by moccah on 2006-01-27
Can you just copy the *mpq files from the DVD and install them ?

---

### Post by proph on 2006-01-30
Sordo, I was wondering if you could post what changes you made in winecfg in order to make it stay within the same folder.

---

### Post by schnabea on 2006-01-31
I just copy all the files from the first cd and then the Installer Tome.mpq files from the other 3 cds in to one single folder and it installs fine. I ddin't have to change winecfg or confed anything and it didn't ask to change cds.

Now if I could only get the game to run with -opengl...

---

