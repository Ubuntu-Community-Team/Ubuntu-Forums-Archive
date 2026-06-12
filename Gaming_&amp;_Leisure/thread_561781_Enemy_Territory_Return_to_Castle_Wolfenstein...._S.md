---
title: "Enemy Territory: Return to Castle Wolfenstein.... Sound Issues on install (no sound)"
date: 2007-09-28
forum: Gaming &amp; Leisure
---

### Post by tolstoyboy on 2007-09-28
hi. i just tried installing Enemy Territory. when i run the game it is all great...runs really smooth graphicwise...however...i have no sound!!  i'm kinda a newb and really have no idea what a problem might be.  

when i installed it asked me twice where to install files...it was defaulting to something like "usr/bin/....."  but when i said ok...it would  tell me i couldn't write to those directories. so instead i just directed both prompts to place the files in a folder i made in my home directory. other than this, the install went fine and normal. 

i checked the system sound and the ingame controls..they are set reasonably...but ...nothing...

does anyone have any suggestions about this? have you encountered this problem?

my system is an acer aspire 5102 notebook:  AMD Turion 64x2 cpu, ATI Xpress 1100 video. running ubuntu 7.04 64bit. 
i'm not sure what sound device or driver it recalls...if that must be known please let me know if it helps.

thank you

---

### Post by Waappu on 2007-09-28
Hi

Try type this on terminal```
sudo sh -c "echo 'et.x86 0 0 direct' > /proc/asound/card0/pcm0p/oss"
sudo sh -c "echo 'et.x86 0 0 disable' > /proc/asound/card0/pcm0c/oss"
```and test if sound works. If yes apply this fix permanetly by typing in terminal```
sudo gedit /etc/rc.local
```and add these lines end of file```
echo 'et.x86 0 0 direct' > /proc/asound/card0/pcm0p/oss
echo 'et.x86 0 0 disable' > /proc/asound/card0/pcm0c/oss
exit 0
```

---

### Post by tolstoyboy on 2007-09-28
Yes! Thank You, it worked right away.  What exactly do those lines enable or do...you don't have to be specific or overtechnical...just trying to learn basic stuff here.

:)

---

### Post by Waappu on 2007-09-28
Hi

Sorry I don't have any idea =)
I find solution to problem from here
[http://www.ubuntu-fi.org/Wiki/Enemy_Territory](http://www.ubuntu-fi.org/Wiki/Enemy_Territory)

---

### Post by asipi on 2007-09-29
It tells the sound system that the et.x86 binary do not need to fully own the soundcard (sure because et never use the input channel of the sound system), and all the sound output can go directly to the mixer.

It is a shame of linux's sound system and the et linux port, because the OSS is very oldfashioned compared to e.g. the alsa sound system

unfortunatelly we have to live with this relic because the fans could not miss ET :) and hope that the solution will be introduced in ET:QW linux port would catcth the limits of the nowadays :)

---

### Post by desicratn on 2009-05-14
I am kinda shocked that in Juanty  this is till an issue...LOL.This solution Still works anyways.

---

### Post by asipi on 2009-05-15
I think it's not Jaunty's fault rather the linux q3 engine's. Pulseaudio is the goal for clean the linux sound mess but it could not solve everything (yet?). I used to hate pulseaudio and my first task for every ubuntu release to kill it in my system. Jaunty was significally better, but ET was a problem (if you also need teamspeak it is an ultimate impossible challenge).

Anyway if one wants to play with "old" sound style games under linux it is better to remove pulseaudio also and use the good old workarounds to make their sounds alive.

For example ETQW has a significant sound delay with pulseaudio with my machine. Without it it is fine. Also I have skype sound problems with pulse and without it it works well. It is a sad story :(
Maybe after some years the linux sound mess will disappear based on pulse developing and new versions of the games (and other softwares). It will cause that we should forget playing the old games (RTCW:ET was released in 2003 :o but still the best fps ;)). E.g. games with ioquake3 engine rather than the old q3 ones has better results (like urban terror, world of padman). Also one of my favorites nexuiz works well with minimal sound delay under pulseausio (guess 0.1 seconds or less).

---

### Post by jasonbauer on 2010-05-17
> **waappu said:**
> hi

try type this on terminal```
sudo sh -c "echo 'et.x86 0 0 direct' > /proc/asound/card0/pcm0p/oss"
sudo sh -c "echo 'et.x86 0 0 disable' > /proc/asound/card0/pcm0c/oss"
```and test if sound works. If yes apply this fix permanetly by typing in terminal```
sudo gedit /etc/rc.local
```and add these lines end of file```
echo 'et.x86 0 0 direct' > /proc/asound/card0/pcm0p/oss
echo 'et.x86 0 0 disable' > /proc/asound/card0/pcm0c/oss
exit 0
```


thank you!!!!! Waapu      ):p

---

