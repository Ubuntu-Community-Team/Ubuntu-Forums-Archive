---
title: "Happy to be here!"
date: 2006-01-11
forum: General Help
---

### Post by Rhino1 on 2006-01-11
I am fairly new to Linux and Ubuntu,  I have managed to partition my NTFS hard drive, install Ubuntu, add Dillo, Sylpheed and Firestarter along with Fluxbox & IceWM.  I am currently surfing at the stately speed of 14.4Kbps on a Conexant/Linuxant dial-up.  The programs I have added allow me to go where I want and arrive on time, maybe not your time, but within limits.  I do have a couple of concerns though - mostly just a preference control for the Synpaptic manager - I can't keep the stats available for longer than a day or two..I need to keep them for at least several weeks - (it takes me approx 30 minutes just to update).  Synaptic also attempts to download the universe file twice (the really big one  - takes 20 minutes to download, minimum).  Can someone point me in the right direcion to adjust this.  

Thanks in advance.  

And please don't bother to tell me to get broadband/dsl etc, it ain't gonna happen anytime soon!

---

### Post by Zelut on 2006-01-11
Well one thing I would suggest is you could remove the deb-src lines (## coment out) from your sources.list.  In most cases you aren't going to need the source packages & this should cut down on your modem work.

sudo nano /etc/apt/sources.list

---

### Post by hscottyh on 2006-01-12
Wish broadband was an option for you......
Couldn't you spend $20 on a 56K modem. That would speed you up by almost 400%!!!!

---

### Post by ranf on 2006-01-12
[QUOTE=Rhino1]I do have a couple of concerns though - mostly just a preference control for the Synpaptic manager - I can't keep the stats available for longer than a day or two..I need to keep them for at least several weeks - (it takes me approx 30 minutes just to update).[/QUOTE]
You should stop the update manager from automatically looking for updates:

System -> System -> Update Manager -> [Preferences] -> [Settings]

---

### Post by Sef on 2006-01-12
Sometimes you can't get a faster line.   My mom is stuck on 28.8 kbps.  She would love to get a faster connection, but where she lives it's not possible.

---

### Post by Rhino1 on 2006-01-12
Thanks to everyone that replied.  

Kuyaedz - I will probably do the comment out of deb/src.

hscottyh - I already have 3 cheap $20 modems installed, no Linux drivers for 2 of them, need serial modem $60+ for something worthwhile.

ranf - I don't automatically update, I have it set to ask first,  synaptic deletes the "not Loaded, new in repository info" usually 2 days after I update manually. 

sef - I can run Windows XP at 56K no problem, I choose not to, though.

---

