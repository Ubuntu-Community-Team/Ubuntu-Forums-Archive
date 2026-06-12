---
title: "video distortion..."
date: 2005-10-04
forum: Desktop Environments
---

### Post by robfindlay on 2005-10-04
I'm using Xine as my defualt player for videos and somtimes for some reason I can't decern every video --including the ones that just worked-- are distorted, almost like th colors are reversed or some of the colors have been replaced with much brighter ones. 

It's kind of phycadelic but not really what I want. As is I have to kill and restart X to
fix this.  

Is there a way to reset ones video codecs without having to kill and restart X ?


Rob

---

### Post by KingBahamut on 2005-10-04
if you have w32codecs installed, you could feasibly remove it and reinstall it. 
apt-get remove w32codecs 
apt-get install w32codes 
What video card do you have / are using?

---

### Post by robfindlay on 2005-10-04
[QUOTE=KingBahamut]if you have w32codecs installed, you could feasibly remove it and reinstall it. 
apt-get remove w32codecs 
apt-get install w32codes 
What video card do you have / are using?[/QUOTE]

It's an intel 915GM, I fear the only fix for this is restarting xorg...the thing i'm trying to avoid.  

Tkns though... 


Rob

---

### Post by ankush_jhalani on 2005-11-17
Same problem here, it only happened after ive installed the xine-totem. Earlier the colors were coming good, but a lot of frame drops and audio-video out of sync problem.
  mplayer interface sucks, and xine is much better but both of them now shouwing bad colors, kinda like reversed. Can someone help.

---

