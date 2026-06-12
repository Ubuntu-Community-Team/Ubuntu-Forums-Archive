---
title: "[SOLVED] 1420n with gutsy xorg-video-intel problems"
date: 2007-08-05
forum: Dell  Ubuntu Support
---

### Post by iggykoopa on 2007-08-05
hey i updated to the gutsy version of xorg-video-intel so i could use compiz-fusion, it ran great but when trying to play video on any player it would not work. I tried disabling compiz-fusion but video still wouldn't play. The output from the players was all similar, Malloc insufficient resources. I was just wondering if anyone else was having similar problems? the only workaround i really tried was setting the video ram thru xorg.conf since i cant find a setting in the bios for it. any help i can get would be great i love compiz but need to be able to watch video's. Oh and i installed the intel driver according to the guide in this forum.

and on a side note the wifi switch does nothing on my 1420n, the wireless is working fine but will drop the connection occasionally, is the wifi switch supposed to turn on and off the wireless in linux or it a software thing for microsoft only?(i changed it in the bios to just turn on and off the wifi not bluetooth or do the wifi scan, but it was behaving the same with the default settings.)

---

### Post by iggykoopa on 2007-08-06
If anyone else has the same problem to fix it I went into MPlayer and in the video preferences set the driver to gl2, now it playes video even with compiz-fusion enabled. Only problem i have is the window borders dont show up on MPlayer correctly about half the time but i can deal with that.

---

### Post by jacob01 on 2007-08-06
im not using gutsy but a similar thing happens to me when i use beryl or any other window manager other than the default i would say the no border thing is a bug. and to report it to get fixed you should report that bug maybe try on the gutsy forum

---

### Post by iggykoopa on 2007-08-06
it only happens with mplayer though, but I'll look around at the other posts. thanks

---

### Post by sciurus on 2007-08-08
What video output device is Mplayer configured to use?

The default for gsteamer-based apps (eg Totem) is configured with gstreamer-properties.

I can't use xv with compiz-fusion, but apparently this is a known problem [http://lists.freedesktop.org/archives/xorg/2007-June/025933.html](http://lists.freedesktop.org/archives/xorg/2007-June/025933.html) . If I use EXA X crashes when I start compiz.

---

### Post by iggykoopa on 2007-08-10
I am using gl2 in mplayer, i cant select gl2 for totem in gstreamer-properties cause its not an option. This isn't just with compiz-fusion tho, even if i disable desktop effects its still says insufficient resources, it seems to be a problem with the xserver-xorg-video-intel drivers.

---

### Post by phynix on 2007-08-11
I had this problem with videos not playing with compiz fusion installed this fixed it

[http://ubuntuforums.org/showthread.php?t=507328&highlight=compiz+totem+playback]("http://ubuntuforums.org/showthread.php?t=507328&highlight=compiz+totem+playback")

I only tried this with vlc and it worked perfectly. I hope this helps. 


-phynix

---

### Post by iggykoopa on 2007-08-12
Thanks i feel really stupid now lol, when i was changing gstreamer-properties to no XV before it still wasn't working because i had totem-xine installed still :( fixed now.

---

