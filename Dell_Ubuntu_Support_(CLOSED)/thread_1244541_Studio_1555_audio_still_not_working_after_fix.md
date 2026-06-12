---
title: "Studio 1555 audio still not working after fix"
date: 2009-08-19
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Kaemka on 2009-08-19
I just installed Ubuntu 9.04 on a brand new Dell Studio 1555. Its an absolutely untouched install apart from having downloaded from the ATI site and installed the restricted driver for the HD 4570 graphics card.

I noticed that sound didnt work, and did my homework to find out that it never worked out of the box on a studio 1555 but there was a fix that worked perfectly. I edited /etc/modprobe.d/alsa-base.conf as sudo and added the line
```
options snd-hda-intel model=dell-m6
```
and rebooted.

However, it didnt work for me. Nothing has changed at all. No login sounds. I installed amarok to try playing mp3s and flash plugin to try youtube. Sound still works perfectly in vista and windows 7.

---

### Post by edwardLS on 2009-08-20
I also have a Studio 1555, and went through the same steps to attempt to correct my sound.  What I eventually found that corrected the problem is the sound system was in MUTE.  I don't have a Ubuntu here at work, so I can't tell you the exact name of the speaker-ICON in 'my' upper right side of the panel.

Hope this helps.

---

### Post by Kaemka on 2009-08-21
Thanks alot for the reply. Also, since you also have a 1555, any news on the brightness-buttons issue?

Sadly, the problem doesnt look that simple to me. It would be nice if anyone would check out this screenshot and see if there is anything wrong:

[http://img12.imageshack.us/img12/6416/screenshotcte.png](http://img12.imageshack.us/img12/6416/screenshotcte.png)


Any help is appreciated. Very much so.

---

### Post by beethree on 2009-08-21
I can't thank you enough for your post!  Even though it didn't work for you, the tweak to alsa-base.conf worked for me.  Thanks again!

---

### Post by edwardLS on 2009-08-24
> **Kaemka said:**
> Thanks alot for the reply. Also, since you also have a 1555, any news on the brightness-buttons issue?

Sadly, the problem doesnt look that simple to me. It would be nice if anyone would check out this screenshot and see if there is anything wrong:

[http://img12.imageshack.us/img12/6416/screenshotcte.png](http://img12.imageshack.us/img12/6416/screenshotcte.png)


Any help is appreciated. Very much so.

I took the cowards way out with the brightness control.  My brightness control would work for a bit after starting up Ubuntu, but in a very short period of time it would stop working.  So, I set the default brightness for 50% so that the system starts up at 50% brightness.  Then if the control works, or not, I simply don't care.

Not a perfect solution, but I am living with it fairly well.

---

### Post by fazillatheef on 2009-08-26
The brightness issue has been raised as a bug in the linux kernel. Someone posted a kernel patch on ubuntu forum.. but that one was not safe.. I think things will be resolved by karmic release

---

