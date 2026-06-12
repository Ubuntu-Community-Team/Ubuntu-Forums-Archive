---
title: "Medal of Honor AND Q4"
date: 2006-02-06
forum: Gaming &amp; Leisure
---

### Post by PandabeaR on 2006-02-06
For some reason when I try and launch MoH and Q4 i get the error 'could not load default.cfg'.

I followed instructions of quake 4(extraction of pk4 files and running installer).

For MoH, I ran the installer and had the cd's inserted... Im not sure it says I should run it on a windows pc and put it on a linux box. But it seemed to install fine with the 'installer' (mohaa-lnx-1.11-beta3.run). Can anyone help me with this problem?:-k

---

### Post by skirkpatrick on 2006-02-07
I've got Q4 running and I don't think I've seen that message.  I looked around in both my ~/.quake4 and /usr/local/games/quake4 and none of them have a default.cfg file.

---

### Post by Unrivaled on 2006-02-07
I got that error before I copied the files from the CDs. (Quake 4)

---

### Post by pmj on 2006-02-07
Perhaps this thread could be of help for getting Quake 4 running: [http://ubuntuforums.org/showthread.php?t=79887]("http://ubuntuforums.org/showthread.php?t=79887")

---

### Post by PandabeaR on 2006-02-08
Yah, I did that and fixed that problem(i think) but now I have a new problem. It says there is a 'segmentation fault' in the gamex86 file... What does that mean?

---

### Post by pmj on 2006-02-08
A segmentation fault means something went very wrong somewhere.

I did a search on the forum again and came up with this: [http://ubuntuforums.org/showthread.php?t=80964]("http://ubuntuforums.org/showthread.php?t=80964")

The last post suggests that removing libsdl1.2debian-all and installing libsdl1.2debian-alsa could solve it.

---

### Post by PandabeaR on 2006-02-08
Ok, I'll try. But mine seems to suggest something to do with OpenGL =\

---

