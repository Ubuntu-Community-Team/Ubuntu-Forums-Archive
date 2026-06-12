---
title: "Ubuntu 9.04 Dell Vostro 1700 Digital Sound Output"
date: 2009-05-18
forum: Dell Ubuntu Support (CLOSED)
---

### Post by maragon5 on 2009-05-18
Hello all:

I recently installed Ubuntu 9.04 on my Dell  Vostro 1700 notebook, 

all seems to be working well with this exception:

The system cannot playback sound via the digital output on the laptop  (The modified 11 pin S-Video like port)

I have a home theater system wired to the additional dongle that  converts the 11 Pin S-Video output to RGB and S/PDIF (MADE BY DELL)

I really enjoy playing my movies on my 50" tv screen which I use as a second display, but the sound is playing from the laptop and I cannot get it to switch over.

Ubuntu recognizes the second display hooked into the S-video port, but I cant seem to get sound to switch over from the laptop speakers to the digital sound out.   

VISTA/ and Windows 7 have no problem detecting the S/PDIF playback once the appropriate sigmatel drivers are installed.

Any suggestions?

---

### Post by zeddock on 2009-06-25
Try this...
Vostro 1700 Sound Audio
Audio works: Speakers; Plugged in; Mic. please be sure that all channels are unmute and risen up. (sudo alsamixer; F5 to show ALL channels; recommended)
turn all up and unmute. Seemed to work for me on 9.04
[http://alerttail.sourceforge.net/dellvostro1700/](http://alerttail.sourceforge.net/dellvostro1700/)
[http://www.linux-on-laptops.com/dell.html](http://www.linux-on-laptops.com/dell.html)

---

