---
title: "Kaffeine under Gnome - Sound acting oddly"
date: 2005-06-26
forum: Desktop Environments
---

### Post by walkeral on 2005-06-26
I've come across a problem which I have been unable to solve through any existing methods.

Basically, I was running Kubuntu, where Kaffeine worked perfectly (mainly for watching DVB). I have now decided to switch to vanilla Ubuntu, and Gnome. Now, Kaffeine is acting rather oddly, in that there is no sound with DVB or any recordings I've made. There's also no sound from MP3 files. Yet, if I play an Ogg Vorbis file, it works perfectly. Also, if I play the Ogg file after trying to play something else, it doesn't work until I reselect the sound driver in the xine engine options.

I've implemented the esd.conf fix as highlighted in the Ubuntu guide, I've got the Multimedia System Selector set to ESD, and Kaffeine set to ESD.

I don't reckon this is a problem with Kaffeine itself as it worked fine under Kubuntu and KDE. Is anyone else running Kaffeine under Gnome and Ubuntu that has got everything working normally? Any assistance appreciated.

---

### Post by walkeral on 2005-06-27
I've narrowed this problem down to the xine engine. I've confirmed that this problem is not to do with the soundcard as the problem is identical on another PC. I've tried using XMMS and gxine as well - It appears that XMMS can play sound fine from any source, whereas gxine does exactly the same as Kaffeine - plays oggs but just skips through mp3s as if it's writing them to the hard drive. The output settings are the same in both applications.

I'll try doing a clean build of lib-xine and gxine later - might just be a missing library somewhere.

---

### Post by walkeral on 2005-07-01
One full build of the latest Xine and gxine later and it works fine. I've also rebuilt Kaffeine on my virtual machine and it seems to work, though I haven't had the chance to try it on the actual PC. Unfortunately it's gone back to crashing repeatedly like before I downloaded the "fixed" package. 

I'd say a lesson learnt and a useful piece of advice for newbies - if it doesn't work from the packages, rebuild it from source, even if it means downloading numerous -dev packages to get all the required libraries.

---

