---
title: "Interesting Sound Problem"
date: 2005-11-07
forum: Desktop Environments
---

### Post by makisupa123 on 2005-11-07
I have a Maudio audiophile 24/96 soundcard.  One of the great things about 5.10 was that it just worked (mostly) using ALSA from the get go.  Digging a little deeper i've been tryin to fix sound in flash applications which is scratchy, jerky, or sounds like its skipping (not sure of the best adjective).  
     Browsing around I found several threads addressing flash sound not wokring at all and eventually discovered that changing the buffer_size in my asound.conf file fixes the problem.  EXCEPT....
     Making that change disables all of my system sounds.  But things like BMP still work -- just no gnome sounds.  After making that edit terminal will show all of the sampling rates/word lengths that it CANT use and then say the card will not work with Esound.  Anyone know how to get the best of both worlds?  OH -- and OSS is NOT the answer.  I use that driver in freeBSD and would rather not mess with it here.

Thanks!!

mak.

---

