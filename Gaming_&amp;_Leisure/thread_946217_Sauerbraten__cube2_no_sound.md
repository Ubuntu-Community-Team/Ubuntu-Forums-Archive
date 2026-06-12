---
title: "Sauerbraten / cube2 no sound"
date: 2008-10-13
forum: Gaming &amp; Leisure
---

### Post by alwayshere on 2008-10-13
i have sound everywhere but not with Sauerbraten i am using ubuntu 8.04 
any ideas ??

---

### Post by alwayshere on 2008-10-13
yes my other linux games are working and wine/windows as well

---

### Post by GSZX1337 on 2008-10-13
Do you have another audio program open? Anything like YouTube, Last.fm, or flash games in your browser? I had that problem, and it turned ouit to be that I had Banshee minimized.

---

### Post by alwayshere on 2008-10-14
no i have none of those problems i have looked into those i wonder what is so different about the sound in sauerbraten from other games ?

---

### Post by wirespot on 2008-11-22
There are seven different libsdl1.2debian-* packages available. Check that you have the one that's appropriate for your sound system (ie. the one ending in -alsa if you use ALSA), or install libsdl1.2debian-all. You probably have the one ending in -oss, which exhibits the issues described before (no multiplexing, so only works when nothing else uses the sound device).

---

