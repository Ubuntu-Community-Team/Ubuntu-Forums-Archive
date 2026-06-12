---
title: "quake2...."
date: 2006-01-13
forum: Gaming &amp; Leisure
---

### Post by akurashy on 2006-01-13
well dunno if any of you got it running but i get this
Do you understand the security implications of continuing?
yes
QuakeIIForge 0.3
using /home/david/.quake2/baseq2/ for writing
couldn't exec default.cfg
execing config.cfg
Console initialized.

------- sound initialization -------
loading oss sound output driver, ok
oss: buffer size is 16384, 8192 samples
sound sampling rate: 11025
------------------------------------
------- Loading ref_softx.so -------
LoadLibrary("ref_softx.so")
No joysticks found
SNDDMA_Shutdown
recursive shutdown
Error: Couldn't load pics/colormap.pcx

---

### Post by Mr_Grieves on 2006-01-13
Never tried it, but:

> 
Error: Couldn't load pics/colormap.pcx


What's that? A file you are missing? Seems so..
Could you put the file or link to where it's supposed to be and things might work.

---

### Post by danoyoto on 2006-01-16
Hey I get the EXACT same error message so please let me know if yuo find a solution.  I will post back on this thread if I find something also.

---

### Post by Iesos on 2006-01-18
I used to have that problem, but its seems too have vanished.
I tried to run quake as a su and then it worked. that is try:

 $sudo wine quake2.exe

worked for me.

---

### Post by sorcererx84 on 2006-01-18
Put [this]("http://www.hot.ee/sorcerer/pak7.pak") pak file into your quake2/baseq2 folder and try again.

---

### Post by vgeddes on 2006-01-21
You probably have not installed the game data. All quake2 derivates need the game data to work properly. You need to copy this data from your Quake2 cd onto your harddrive, in a location where the executable can find it.

The *quake2-data* package (in multiverse/universe) can automate this task for you

---

### Post by gil-galad on 2006-01-21
Try this installer.  It can get the data from the retail cdrom or it can install the shareware version for you.  

[http://liflg.org/?catid=6&gameid=55](http://liflg.org/?catid=6&gameid=55)

---

