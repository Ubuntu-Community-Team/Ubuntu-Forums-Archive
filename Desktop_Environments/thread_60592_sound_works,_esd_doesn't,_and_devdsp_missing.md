---
title: "sound works, esd doesn't, and /dev/dsp missing"
date: 2005-08-28
forum: Desktop Environments
---

### Post by jpkotta on 2005-08-28
My problem is this:  My sound works, but not the way I want.  I hear the drum thing in gdm.  I can get output from xmms via the ALSA plugin, but not esd.  I can get output from xine via ALSA and esd plugins (weird).  ```
ps -ef | grep -iE 'esd|sound'
``` returns nothing.  When I try to run esd or esdplay, they tell me that /dev/dsp is missing, and indeed it is.  I usually don't run gnome, just fvwm, but the same problems exist in both.

I've read all sorts of forum posts and HowTos, etc., with nothing that worked for me.  I really like Ubuntu, this is essentially the last issue I have to resolve.

---

### Post by arnieboy on 2005-08-28
[QUOTE=jpkotta]My problem is this:  My sound works, but not the way I want.  I hear the drum thing in gdm.  I can get output from xmms via the ALSA plugin, but not esd.  I can get output from xine via ALSA and esd plugins (weird).  ```
ps -ef | grep -iE 'esd|sound'
``` returns nothing.  When I try to run esd or esdplay, they tell me that /dev/dsp is missing, and indeed it is.  I usually don't run gnome, just fvwm, but the same problems exist in both.

I've read all sorts of forum posts and HowTos, etc., with nothing that worked for me.  I really like Ubuntu, this is essentially the last issue I have to resolve.[/QUOTE]
why do u like esd so much? alsa is way much more sophisticated and also supports duplex sounds. esd doesnt. its on its way out.

---

### Post by jpkotta on 2005-08-29
Maybe I'm confused, but I thought esd was a layer on top of ALSA.  I think GNOME uses esd as it's sound server as well.  I use esd precisely because I can multiplex sound with it.  Whenever I use ALSA output plugins, they hog the sound card.  

I guess the problem I'm really trying to solve is this:  I want to be able to run xmms or xine and be able to use a command line utility like esdplay to play a .wav file at the same time.

---

### Post by jpkotta on 2005-08-29
I installed artsplay and artsd.  I had some .au files that arts choked on, so I installed sox to convert them.  God, it was awful.  I eventually figured out that I have to do this:```
sox file.au file.ogg && sox file.ogg file.wav
``` in order to get artsplay to play it.  One reason why I prefer esd to arts.  

Anyway, I also hacked sound support into Mathematica with esdcat, so tomorrow I get to see if artscat works too.  

I am still very interested in why I have sound with no /dev/dsp or how to create it.

---

### Post by jpkotta on 2005-09-07
esd now works.  This is the command to create /dev/dsp:
```
sudo mknod /dev/dsp c 14 3 && sudo chmod 777 /dev/dsp
```

Also, arnieboy, alsa and esd have completely different functions, and can be used simultaneously.  alsa is a low level abstraction layer.  It replaces the open sound system (oss), which is indeed on its way out.  esd and arts are sound servers.  They mix sound streams together, then dump them to alsa or oss so that the streams can be multiplexed.  alsa, by itself, doesn't support multiplexing any more than oss, AFAIK.

I'll post a topic on sound in Mathematica soon.  It's already on the message board for Mathematica, but that board sucks.

---

