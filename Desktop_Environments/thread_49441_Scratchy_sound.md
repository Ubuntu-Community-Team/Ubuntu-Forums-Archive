---
title: "Scratchy sound"
date: 2005-07-16
forum: Desktop Environments
---

### Post by Sheep Me on 2005-07-16
My sound is scratchy, no matter if it's played from CD, mp3 or mpc, with XMMS, MPD or CD Player, through ESD, OSS or ALSA.

I thought this guys problem sounded a bit like mine:
[http://ubuntuforums.org/showthread.php?t=35613](http://ubuntuforums.org/showthread.php?t=35613)
So I tried out the solution to his problem, but it didn't help me.

I going crazy, not being able to listen to my music. :-?

---

### Post by Sheep Me on 2005-07-17
It's suggested that my software mixer's volume is turned up too high, but nothing I do will turn down the volume. I've tried the volume control in the Gnome panel (not saying that's the right one), aumix and alsamixer. Nothing gets the volume down, not even alsamixer when using ALSA as output in XMMS. How can that be?

---

### Post by Boggles3 on 2005-07-17
hey if you go into alsa mixer in your console(type alsamixer) and scroll to the right with arrow key you should eventually see something called digital out or something like that... its muted by default and some cards need it not to be...
check that  :)

oh ya and what card do you have ??? if its audigy 2 then there might be more to do than that but just try that for now

---

### Post by Sheep Me on 2005-07-17
Thank you for your suggestion.

Nothing I do in alsamixer has any effect, but turning on and off PCM. Everything else I can turn up and down, on and off and nothing happens.

But I did look for something along with "digital out" - the only thing that came close was a thing called "IEC958 P", which I can switch from analog to digital. But like with all the rest, nothing happens.

About my "card" (onboard AC'97), alsamixer says:
Card: Intel ICH5
Chip: C-Media Electronics CMI9761

I'm almost certain, that when I first installed Ubuntu, the volume slider in the Gnome panel had an effect on the volume, and now it doesn't - along with everything else.

---

### Post by NaitoNeko on 2005-07-17
[QUOTE=Boggles3]hey if you go into alsa mixer in your console(type alsamixer) and scroll to the right with arrow key you should eventually see something called digital out or something like that... its muted by default and some cards need it not to be...
check that  :)

oh ya and what card do you have ??? if its audigy 2 then there might be more to do than that but just try that for now[/QUOTE]


I had the same problem and I muted some crap in the alsamixer and all is perfectly normal again ..... Thnx

---

### Post by Sheep Me on 2005-07-18
I think my problem is that the sound is clipping, because the volume of the software mixer is set too high. It's only scratchy when high-volume passages occurs in a song. I just can't adjust the software mixer, not with alsamixer, not with anything.

I don't know if I installed a program that messed things up (in that case, I'm almost sure it was done with apt-get/Synaptic). Perhaps I made a wrong configuration along the way. I really hope it's one of the two, because I'm going to reinstall Ubuntu soon, and I won't have this problem again. :smile:

---

### Post by Sheep Me on 2005-07-18
A reinstall of Ubuntu didn't work. It gave me the exact same symptoms.

---

### Post by Sheep Me on 2005-07-18
Update: Fedora Core 4 doesn't give me scratchy sound, and alsamixer works to some extend (the PCM volume is adjustable, the master isn't).

---

### Post by souki on 2005-07-18
hello,

I don't know if we have the same issue but polypaudio solve my problem (digital sound distorsion with hoary). Don't ask me why, I just don't understand how pure-alsa is affected by this (sound buffer?)

if you install polypaudio it will remove the esound package (polypaudio is an esound server replacement). If it does not work, you can revert back to esound by reinstalling it. But, in my opinion, polypaudio is mutch better than esound

---

### Post by Sheep Me on 2005-07-18
Thanks, I'll try that. In the mean time, another update:

In Fedore Core I only tried to play a CD (which gave me scratchy sound in Ubuntu). The fact that it didn't in Fedore Core, may have had something to do with the way the sound travels from CD to speakers (I'm told - Ubuntu may do it differently from Fedore Core.

Regardless of the value of my Fedore Core test results, I have some new results from Knoppix, and Knoppix scratches the sound just as much as Ubutun (this time I tried with an mp3-file). So I guess it's a more general problem related to Linux. (Windows doesn't scratch the sound - I've just tried again to make sure.)

---

### Post by Sheep Me on 2005-07-18
[QUOTE=souki]I don't know if we have the same issue but polypaudio solve my problem (digital sound distorsion with hoary).[/QUOTE]I FUCKING LOVE YOU MAN! ;) That solved my problem. The question now is why.

---

### Post by souki on 2005-07-19
thank you,

I've spent a lot of time on this, I just don't understand the relation

---

### Post by Sheep Me on 2005-07-19
Damn! It didn't completely solve the problem. Only the breezy version of polypaudio fixes whatever's wrong, the hoary version doesn't.

Here's the deal...

With a completely fresh install of Ubuntu, XMMS being the only addition/modification, this is what I get: XMMS delivers scratchy sound, whether I use esound, oss og alsa as output.

With the breezy version of polypaudio added to the above install, this is what I get: XMMS delivers scratchy sound, only when using oss as output. The sound is clean as glass, if I use esound (which I guess with the absence of esd is using polypaudio) or alsa as output.

What the hell is the problem. :neutral:

---

### Post by DancingSun on 2005-07-19
I just turn down the PCM volume...until somebody can determine a reliable fix.

---

### Post by Sheep Me on 2005-07-19
Perhaps that would work, the sound seems to be clipping, but alsamixer and any other tool to turn down the volume doesn't work. I can push all the sliders up and down, it makes *no* difference. This and the scratchy sound are my two problems. I'm sure they are related, because installing the breezy version of polypaudio solved both.

---

### Post by Sheep Me on 2005-07-20
In an hour the DVD image for Debian Sarge is ready for installation. I'll try that, and if it's got the same problem, or I can't set it up properly, I really don't know where to turn or what to do.

I've tried asking in my countrys Unix newsgroup, I've tried asking in linux.debian.user, I've tried here. Any other ideas? :|

---

### Post by souki on 2005-07-20
hey, maybe my config could help

I got digital saturation with esound ("scratchy sound") so, after hours trying several things I've switched to polypaudio
I use polypaudio with hoary+backports and everything works perfectly, here are my packages
```
dpkg -l|grep polypaudio
ii  libpolyp0           0.7-0ubuntu5        Library for the polypaudio sound server
ii  polypaudio          0.7-0ubuntu5        Pluggable sound server
ii  polypaudio-alsa     0.7-0ubuntu5        ALSA modules for the polypaudio sound server
```
I've tried xmms:
- esound output ok
- alsa output ok
- oss output error: cannot play (I think this has nothing to do with the current problem)

I don't use dmix and have no asound.conf nor .asoundrc file

here is my /etc/esound/esd.conf
```
[esd]
auto_spawn=0
spawn_options=-terminate -nobeeps -as 5
spawn_wait_ms=100
# default options are used in spawned and non-spawned
default_options=

```
my guess is that esound is saturating the audio buffer so any method to play a sound get saturated
I LOVE polypaudio !!!

---

### Post by Sheep Me on 2005-07-20
[QUOTE=souki]hey, maybe my config could help[/QUOTE]It didn't work, but thank you anyway.

Have you ever had trouble with alsamixer not working?

Have you installed any alsa related packages?

---

### Post by souki on 2005-07-20
so bad :(

here is some packages I have
```
dpkg -l | grep alsa
ii  alsa-base           1.0.8-4ubuntu4      ALSA driver configuration files
ii  alsa-utils          1.0.8-1ubuntu1      ALSA utilities
ii  gstreamer0.8-alsa   0.8.8-1ubuntu4      ALSA plugin for GStreamer
ii  libesd-alsa0        0.2.35-2ubuntu2     Enlightened Sound Daemon (ALSA) - Shared libraries
ii  libpt-plugins-alsa  1.8.4-1             Portable Windows Library Audio Plugin for the ALSA Int
ii  polypaudio-alsa     0.7-0ubuntu5        ALSA modules for the polypaudio sound server
```

---

### Post by Sheep Me on 2005-07-21
Yeah. I had the same packages. I installed Debian Sarge now, and it had no problem with the sound, so I think I'm going to stick with that.

But thanks *a lot* for trying to help.

---

### Post by Ceebo on 2005-08-31
i have just the same problem. when i put pcm down , scrachy sound dissapear
plz help :|

---

### Post by tropican8 on 2005-11-11
[QUOTE=Sheep Me]Regardless of the value of my Fedore Core test results, I have some new results from Knoppix, and Knoppix scratches the sound just as much as Ubutun (this time I tried with an mp3-file). So I guess it's a more general problem related to Linux. (Windows doesn't scratch the sound - I've just tried again to make sure.)[/QUOTE]

Could it be a problem with Debian-based distros in general?  Knoppix and Ubuntu are both based on Debian.  Either way, I have the same sound card and the bug is a pain.  Also I tried using Winamp and Foobar2000 under wine and I also get the same scratching sounds (crystal clear in windows).

---

### Post by nchase on 2006-09-14
Turned down my PCM volume a bit and it appears to have resolved this issue. That's a good enough fix for me. Thanks all.

---

### Post by roningaijin on 2007-10-03
I have an original Audigy with the Emu10K1 chip, and the second to last column in alsamixer was "Audigy A".  After I muted it, scratchiness was gone.

Thanks!  

...now to get steam to work under wine.

---

