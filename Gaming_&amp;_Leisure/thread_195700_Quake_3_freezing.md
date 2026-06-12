---
title: "Quake 3 freezing"
date: 2006-06-13
forum: Gaming &amp; Leisure
---

### Post by christooss on 2006-06-13
Hello

When Im playing Quake 3 arena. Often whole system freezes. Only solution is hard reset.

Did any of you had such problems.

proc ram temp are normal. So overheeting isn't a problem

---

### Post by toddedw on 2006-06-28
I have the same issue with Quake 3 freezing, but it only freezes when I have my sound enabled. I have to issue the following command to get my sound to work.

<code>echo "quake3.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss</code>

When I do this Quake 3 freezes randomly during play and I have to reboot my system. Of course, when I don't do this I have no sound, but quake 3 runs fine.

I hope this helps. I would like to fix this problem as well.

---

### Post by crane on 2006-06-28
If sound is suspect then try running quake3 at lower sound quality. I believe you can change this in the in-game menus.
 Have you checked your log file for the system and Xserver? Maybe there is some clue there. Maybe check or xorg.conf and make sure all is in order. glcore and dri commented out?
Just a couple of quick thoughs. If I think of anything I will let you know.

---

### Post by sorcererx84 on 2006-06-29
I had the same problem. Try using icculus.org/quake3. It uses OpenAL for sound.

---

### Post by EPOX123 on 2006-06-29
Next time use joss for quake 3 audio.

Try to compile this program it got my m-audio audiophile 2496 to work.

[http://www.craknet.net/joss/](http://www.craknet.net/joss/)

I made a deb pack dont have a place to upload it.

---

### Post by christooss on 2006-06-30
Quake 3 stoped freezing when I changed my graphic card from Ati to Nvidia

---

