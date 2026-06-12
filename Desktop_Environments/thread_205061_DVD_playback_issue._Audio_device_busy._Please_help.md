---
title: "DVD playback issue. Audio device busy. Please help."
date: 2006-06-27
forum: Desktop Environments
---

### Post by kpkeerthi on 2006-06-27
I have a very annoying issue playing DVD movies. After I insert a DVD, totem  plays fine till the main menu (movie menu) is reached. The moment I click on 'Play' from the DVD menu or select any 'Scenes', it just stops with "The audio device is busy. Is another application using it?" and won't proceed anymore. I tried mplayer, gxine but no luck - these two won't even reach upto the movie menu. 

I was able to play DVD movies without a problem... seems like a recent update should have broken it.  

Can someone please help be debug this and isolate the problem? I checked syslog and could find nothing unusual. Also started totem from command-line and it prints nothing more than "The audio device is busy. Is another application using it?" 

I'm going insanely mad about the issues cropping day after day killing my time fixing the problems instead of being productive. Need to vent. Sorry.

---

### Post by kpkeerthi on 2006-06-27
OK. back on track. it was the bmpx player. I purged it and everything is back to normal.

---

