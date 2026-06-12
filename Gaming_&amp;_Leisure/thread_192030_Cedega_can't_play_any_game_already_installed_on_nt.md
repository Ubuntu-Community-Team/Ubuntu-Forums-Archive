---
title: "Cedega: can't play any game already installed on ntfs"
date: 2006-06-08
forum: Gaming &amp; Leisure
---

### Post by flapane on 2006-06-08
Hi
I installed cedega 5.1, fglrx 3d is enabled (6000fps on glxgears), and I added the "exec" option in fstab to my win partition to let already installed games run on cedega.
Anyway I can't play any game on ntfs. I tried diabloo2lod,gta,themehospital,thesims and so on. I can see only a black screen
P.S I tried to install directly in linux tomb raider3, and it worked...
but I need to run previously installed games from my ntfs partition!

---

### Post by WakkiTabakki on 2006-06-08
I'm guessing it's any of the following two reasons
* On install, the game writes keys to the registry. Since tha game was installed under windows, those keys have been written to the windows registry (and won't show up for wine)
* The game needs to write to the game folder (settings, savegames, temp files etc) and linux (usually) can't write to an NTFS-partition

Solution: Simply install the game under linux...

/N

---

### Post by flapane on 2006-06-08
i even tried with command&conquer tiberian sun, which works wonderfully in normal WINE, directly from ntfs

---

