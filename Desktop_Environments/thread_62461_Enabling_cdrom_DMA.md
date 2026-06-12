---
title: "Enabling cdrom DMA"
date: 2005-09-04
forum: Desktop Environments
---

### Post by HolyShnikes on 2005-09-04
I seem to be having some problems with enabling my cdrom dma.  When I type in sudo hdparm -d /dev/cdrom to check and see if my cdrom DMA is enabled it says that it is off.  However when I go to sudo kwrite /dev/hdparm.conf (or whatever it is I dont remember off the top of my head) it says that /dev/cdrom DMA = on.  What the heck is going on?  Anyone have any answers for this??

Thanks 

::HS::

---

### Post by HolyShnikes on 2005-09-04
Ok, I got it enabled....but I thought that would enable my being able to play CD's.  Now does anyone know how to get the CD/DVD player to actually play music or movies (with sound).

---

### Post by codejunkie on 2005-09-04
[QUOTE=HolyShnikes]Ok, I got it enabled....but I thought that would enable my being able to play CD's.  Now does anyone know how to get the CD/DVD player to actually play music or movies (with sound).[/QUOTE]
by default ubuntu doesn't play protected formats because of copyright restrictions checkout [www.ubuntuguide.org](www.ubuntuguide.org) for instructions on enabling support for mp3 dvd etc.
edit: here is direct link to the section that shows how to install multimedia codecs like mp3 [http://www.ubuntuguide.org/#codecs](http://www.ubuntuguide.org/#codecs)

---

### Post by HolyShnikes on 2005-09-05
Ok I have the CD/DVD player working only with Xine though.  None of the other programs will run it.  And in Xine if I turn the volume up too loud I get this horible loud pitch like a microphone is too close to the speaker...

---

