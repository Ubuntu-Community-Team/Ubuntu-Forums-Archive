---
title: "Poor totem playback"
date: 2005-04-19
forum: Desktop Environments
---

### Post by cannibalbob on 2005-04-19
Totem gives jerky playback for video files (havent tried dvd yet).  I installed w32codecs, and dma is on for hda... any other ideas?
thanks,
cannibalbob

---

### Post by Roptaty on 2005-04-19
I guess you have installed totem-gstreamer? Try installing totem-xine instead...

---

### Post by cannibalbob on 2005-04-19
you mean uninstall totem-gstreamer and install totem-xine?

---

### Post by cannibalbob on 2005-04-19
ah, never mind, i see one uninstalls the other.

---

### Post by Stormy Eyes on 2005-04-19
Get rid of totem altogether. **sudo apt-get install vlc** and you can play DVDs and more video formats.

---

### Post by Morimando on 2005-04-19
Why not stick to good old Mplayer? I just love it..

---

### Post by fat_larry on 2005-04-19
Everyone around here seems to have a different method for installing MPlayer....

---

### Post by Sonic-NKT on 2005-04-19
hmm totem xine works nice for me..
but i have problems with playing DVD.. its not smooth. other MPEG2 files are.
also.. is it possible to start mov or RM files on totem?

---

### Post by jpvcx on 2005-04-19
[QUOTE=Sonic-NKT]hmm totem xine works nice for me..
but i have problems with playing DVD.. its not smooth. other MPEG2 files are.
also.. is it possible to start mov or RM files on totem?[/QUOTE]

Are you sure that DMA is on for your dvd drive? (In a terminal type "hdparm /dev/hdc" without the "" IIRC)

---

### Post by j_baer on 2005-04-19
Gstreamer video is just not ready ...

Follow this link [http://www.ubuntuforums.org/showthread.php?t=17727](http://www.ubuntuforums.org/showthread.php?t=17727) and install totem-xine.

There are some scripts which can assist in the installation of win32 codecs and the dvd decoder as well in the howto section.

When you are done you will have have a multimedia system that will play just about anything.

Cheers ...

---

### Post by Sonic-NKT on 2005-04-19
hehe using_dma is off..
so how to activate it?
Thanks..

---

