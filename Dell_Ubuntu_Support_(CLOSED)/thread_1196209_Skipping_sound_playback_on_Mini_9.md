---
title: "Skipping sound playback on Mini 9"
date: 2009-06-24
forum: Dell Ubuntu Support (CLOSED)
---

### Post by kingducttape on 2009-06-24
Just got my new Mini 9 (Vostro A90 technically) yesterday!  Running a fresh install of UNR 9.04.  

I'm having an issue where sound playback skips slightly forward every 30 seconds or so.  Happens both in Songbird (from files on disk and from Last.fm radio) and Firefox (playing music from Pandora).  Tried increasing streaming buffer size in Songbird, no change.  Tried various other fixes, including the general pulseaudio fixes guide [here]("http://ubuntuforums.org/showthread.php?t=789578") with no luck.

Anyone have any ideas?  I plan on using this machine primarily for music-related things, so this is kindof a big problem for me.  Thanks! :)

---

### Post by james_xxx on 2009-06-26
I am having the very same issue on my Mini 9. I am not sure when it started. Audio had worked flawlessly until some time in the last week or so.


Would appreciate any assistance.

(I should add that I am using a standard installation of Ubuntu Jaunty, not Ubuntu Netbook Remix. I don't think this problem has anything to do with UNR, so perhaps this thread should actually be listed under a different category.)

---

### Post by james_xxx on 2009-06-26
I just removed pulseaudio, and that solved the issues with skipping that I was experiencing on my Mini 9.

Just remove pulseaudio, and reboot. 

```
sudo apt-get remove pulseaudio
```

Let me know whether or not this helps.

Peace.

---

### Post by dabnpits on 2009-07-01
I'm having the same issue running ubuntu netbook remix on my dell mini 9. Skipping in Last.fm and RythmBox regardless of buffering settings. Only very small skips, but enough that I notice and it's annoying. 

I'll see if removing pulseaudio fixes things...

Update: Success! Removing pulseaudio as instructed by james_xxx fixed the skipping completely! Thanks james_xxx!

---

### Post by rockin_goliath on 2009-07-02
I am also having this problem, but I don't think removing pulseaudio is the solution. Yes, it gets rid of the problem, but I don't like making such a large deviation from the default setup of Ubuntu.

Does anyone know if some updates came in a little while ago that might have caused this? Perhaps changing some setting in /etc/pulse/daemon.conf might do it.

---

### Post by james_xxx on 2009-07-06
As far as I have been able to discover, removing pulseaudio is about your only option at the moment.

I'm not too sure exactly how deviant removing pulseaudio would really be. It's not been around all that long, and there are still many people choosing not to use it (usually due to hardware compatibility issues, as in our case). It still isn't used in Kubuntu, either.

If you do figure out how to get pulseaudio working again, however, please post how you managed to get that done!

Peace.

---

### Post by rockin_goliath on 2009-07-07
From my limited experience with the usage of pulseaudio, its problems really stem from ALSA and not from pulseaudio itself; pulseaudio is really just exposing a lot of ALSA bugs as it matures.

I've been playing around with /etc/pulse/daemon.conf a bit, with no success yet, but I'll let everyone know if I find something.

---

### Post by shiningkenmonster on 2009-07-07
it has been known for a while that since review of Ubuntu 8.04 - that Canonical did a poor job maintenancing the pulseaudio drivers.  even on Ubuntu 9.04 netbook review edition.

---

### Post by rek075 on 2009-07-08
9.04 never always had this problem. There was an update a couple weeks ago or so that screwed up. Anyway, its annoying as hell... I hope they fix it soon.

---

### Post by james_xxx on 2009-07-17
OK, I just finished installing the pulseaudio that came down with the recent upgrades, and would like to know whether or not any of you have seen improvements. 

On my part, I have only had the chance to do a limited amount of experimenting. While listening to somafm streaming over the last few minutes, I would have to say that things have improved a bit (there is still some 'skipping', but not nearly as much), but are still not back to where things were in the earlier stages of jaunty's life, at which time many of us were having no issues with pulseaudio.

Peace.

---

