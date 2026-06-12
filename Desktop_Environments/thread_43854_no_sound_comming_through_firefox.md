---
title: "no sound comming through firefox"
date: 2005-06-23
forum: Desktop Environments
---

### Post by rdking on 2005-06-23
I can't seem to get any sound to come through firefox.  I don't know where to look to evaluate the problem.  Any help would be great.  All Other Applications seem to run sound fine (in  videos and ogg, mp3) through totem or vlc and music through rthymbox, xmms, etc.  For instance no sound at homestar runner....now we can't have that

---

### Post by piedamaro on 2005-06-23
In don't know if it's still the case, but FF used esd to play sound, so you need esd running.
(I had to make a symlink too, else it won't find the lib).

---

### Post by rdking on 2005-06-23
can you elaborate, I'm pretty new to linux

---

### Post by flankk on 2005-06-23
System -> Preferences -> Multimedia Systems Selector
In the "Audio" tab choose ESD as the default output sink.

```
sudo ln -s /usr/lib/libesd.so.0 /usr/lib/libesd.so.1
```

Also, this is a Flash plugin issue, Firefox is irrelevant.

---

### Post by kabars_edge on 2005-07-01
Flankk,  thanks so much for you input.  I'm a seasoned linux user, but have little experience in the desktop OS realm, I've been using linux for servers for years, but would not have figured that out.  Thanks a bunch.   Kabars_Edge

---

### Post by DiGiTaLFX on 2005-07-23
Wow it works! Cheers for the info here.

---

### Post by Spudgun on 2005-08-05
I've followed Flankk's tips, but I still don't get sounds in Flash movies :(

---

### Post by wadesmart on 2005-08-06
08062005 1744 GMT-5

I checked this and I already have the ESD checked. But I still do not have sound in flash. 

Wade

---

### Post by Prog on 2005-08-10
Same here.  A rather annoying problem indeed.  Anyone know the fix yet?

---

### Post by EpiLePTiC FaiRY on 2005-08-10
[QUOTE=flankk]System -> Preferences -> Multimedia Systems Selector
In the "Audio" tab choose ESD as the default output sink.

```
sudo ln -s /usr/lib/libesd.so.0 /usr/lib/libesd.so.1
```

Also, this is a Flash plugin issue, Firefox is irrelevant.[/QUOTE]
 At last, something that worked!

For those for whom the sound is still working, I did a few things before I used this link command and they might be stopping your systems from playing sound.

The sound output must be ESD

sudo gedit /etc/mozilla-firefox/mozilla-firefoxrc
FIREFOX_DSP="none"

Save it. Save it in your own home directory as well as .mozilla-firefoxrc and .firefoxrc (I'm sure one of these is correct, I haven't deleted to check).

chmod 666 /dev/snd/*

Obviously restart and try FF at each stage to see if you actually need to do all those steps.

I remember doing a lot more than this from hundreds of google results, but these are the ones that were mentioned most often.

---

