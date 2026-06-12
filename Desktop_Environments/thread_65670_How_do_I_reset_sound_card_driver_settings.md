---
title: "How do I reset sound card driver settings?"
date: 2005-09-14
forum: Desktop Environments
---

### Post by DancingSun on 2005-09-14
I've recently bought a Soundblaster Live! (emu10k1) soundcard in an attempt to simplify sound setups and solve some of my sound problems with Ubuntu.

I have an Altec Lansing speakers setup that can take digital signals via a coaxial cable, so I decided to only connect to the "digital out" jack on the back of the soundcard.  The first time that I boot up the computer with the soundcard, sound worked nicely through the digital out connection.  I then wanted to try out the dolby digital capabilities of my speaker system, so I decided to play some AVI files with AC3 audio encoding.  Unfortunately, I heard nothing.  So I decided to fiddle around with the settings in Totem-gstreamer and GXine.  But I still couldn't get the Dolby Digital light to turn on.  I tried messing with the volume control applet, but still nothing.

After a while, I gave up and decided to surf the internet.  Strangely, I noticed the Dolby Digital light was turned on!  However, this time I had no sound at all.  No system sound and no music.

My guess is that the easiest way to fix this is to revert the sound settings in the volume control applet.  But since there are so many soundblaster volume settings, I couldn't remember what changes I made.  Does any one know how to reset to the default settings?

---

### Post by mrashley on 2007-09-27
Me too please.

---

### Post by BobLand on 2007-09-27
I seriously doubt that resetting controls will help.  However, here's where the master volume contol is:  

Open a terminal window.  On the very top left menu bar click on 
```
Applications
Accessories
Terminal
``` and type in ```
alsamixer
```
Make sure the sliders are up or on.  Most likely they will be.  If not, adjust them.  

If you still don't have sound then keep reading.

There are a number of users, myself included, that suffer when some unknown thing gets tweaked or something in an update causes sound to go dead.  I've found that running a few commands will often get it back.

Firstly, go [_[COLOR="Red"]here[/COLOR]_]("http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound") to get an understanding of how sound works.  Most likely, this will fix your problem.
Unfortunately, your sound will probably go dead again so go [_[COLOR="Blue"]here[/COLOR]_]("http://ubuntuforums.org/showthread.php?t=205449&highlight=comprehensive+sound") to see me get unraveled every time my sound goes out, including possible causes and fixes that work consistently for me.

bobland

---

### Post by mrashley on 2007-10-06
It occurred me to check System -> Preferences -> Sound.

In there I found various settings were put to "automatic" so I changed those all to ALSA, which seems to have solved my problem. 

Thanks for everyones help.

---

