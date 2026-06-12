---
title: "can't mount recording device (usb)"
date: 2009-02-25
forum: General Help
---

### Post by Mzwo on 2009-02-25
hi,

having problems with a edirol roland r-09hr digital recorder. nautilus shows the device as usb drive, but i can't mount it - not doing a "right click => mount", in any case. when trying to open the drive, nautilus tells me "unable to mount location - can't mount file."

sorry if this question crops up frequently. i've tried searching the forum, but didn't find anything that would help.

running hardy 64 studio.

many thanks,

Mzwo

---

### Post by heindsight on 2009-02-26
Try opening a terminal and do:
```

sudo mkdir /media/LABEL
sudo mount /dev/disk/by-label/LABEL /media/LABEL
```
(where LABEL is the name Nautilus shows for the device) See if that produces any error output.

---

### Post by Mzwo on 2009-02-26
thanks, will do and report back.

Mzwo

---

### Post by buskerjoe on 2011-10-07
so did it work for you? i can't mount my edirol RH-09HR either. love the sound, but i need to put the files on my PC. 
   opening a terminal and typing commands is something i've never done.

---

