---
title: "Vostro 220s upgraded graphics card - NO SOUND"
date: 2009-07-22
forum: Dell Ubuntu Support (CLOSED)
---

### Post by srnupsen on 2009-07-22
Dear community,

I hope you'll be able to help me, because I have no hair left to pull out :)

Recently I upgraded my Vostro 220s, running 9.04, with a Sapphire Radeon HD 4650 graphics card. However, since then I have not been able to get ANY sound from my PC. I've been searching tons of forums, and have got some clues, but I'm not technically competent enough to sort it out on my own.

I ran the alsa-info, script: "Your ALSA information is located at 

[http://www.alsa-project.org/db/?f=eaa0720d9ca51fce7af1f113b51721b18e3285e4](http://www.alsa-project.org/db/?f=eaa0720d9ca51fce7af1f113b51721b18e3285e4)


Please let me know if you need more info.

EDIT: I have a hunch that both audio outputs use the same module (snd-hda-intel), but I haven't found out how to fix it. I would like to try disabling the HDMI one to see if I could get the onboard sound working. 

Best regards from Norway,
Håkon M.E. Sundaune

---

### Post by srnupsen on 2009-07-24
Too bad nobody was able to help me. I had to resort to installing Windows XP again, as my job depends on being able to listen to sound files. I really, really love Ubuntu (writing this from my laptop running 9.04 with absolutely NO problems, wireless internet included) but it really is a shame that sound is an absolute f...up. 

It's a jungle of modprobe, drivers, pulseaudio, alsamixer, oss, several mixer software solutions, recompiling from scratch and fumbling around out there. I hope it'll get fixed in the future, and I wish I was able and knew enough about coding to help.

[COLOR="Magenta"]Still open for tips to solve this so I can reinstall Ubuntu, though :D[/COLOR]

---

### Post by intrepid brian on 2010-10-13
Not sure if this will help, but I just got sound to work on my vostro 220s after ubuntu 10.10 install.  All I had to do was install gstreamer0.10-xxx codecs.  Go to Applications - Ubuntu Software Center and search for "gstreamer"

---

