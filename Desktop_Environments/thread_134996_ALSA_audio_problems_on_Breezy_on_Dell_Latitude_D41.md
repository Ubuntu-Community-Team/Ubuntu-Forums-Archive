---
title: "ALSA audio problems on Breezy on Dell Latitude D410"
date: 2006-02-23
forum: Desktop Environments
---

### Post by jchau on 2006-02-23
This isn't critically important, but I can't seem to get the Master Playback Volume control to affect headphone volume.  This control only seems to adjust speaker volume.  I can control the volume of the headphone with the Playback Headphone volume control and the Playback PCM volume control, but these volumes are not affected by my volume buttons (It will be a lot more convenient for me to just tap my volume buttons than to open the volume control).  For example, I can press mute and my music will still play through the headphones.  Is there a way to make the master volume control change the headphone volume too?

FYI, I use the gnome-volume-control & the volume control applet in Gnome

Also, I have a microphone that is too quiet.  I already set the microphone capture volume to max and I enabled Mic Boost (+20dB).  Is there any additional way to increase the microphone volume?

Thanks!

---

### Post by jchau on 2006-09-30
I've been using Dapper for a while now & the problem is still there.  Is this a bug or an annoying feature? Should I file a bug report?  Is anyone else having this problem or is it only me?

---

### Post by sirozha on 2007-01-30
> **jchau said:**
> I've been using Dapper for a while now & the problem is still there.  Is this a bug or an annoying feature? Should I file a bug report?  Is anyone else having this problem or is it only me?

I just ran into the same problem, and I also noticed that the "headphones" jack on the media base for Dell Latitude D410 doesn't ouput any sound whatsoever. The "headphones" jack on the D410 itself, outputs sound in very low volume. The built-in speaker volume , however, can be controlled in in software or even using the volume buttons on the D410 without any issues. I'm running Ubuntu 6.10, which I upgraded to from Ubuntu 6.02 (not a clean install of Ubuntu 6.10). I never tried to output sound through either headphone jack when I was running Ubuntu 6.02, so I don't know if this issue exists there. 

Thanks!

---

### Post by jchau on 2007-01-31
> **sirozha said:**
> I just ran into the same problem, and I also noticed that the "headphones" jack on the media base for Dell Latitude D410 doesn't ouput any sound whatsoever. The "headphones" jack on the D410 itself, outputs sound in very low volume. The built-in speaker volume , however, can be controlled in in software or even using the volume buttons on the D410 without any issues. I'm running Ubuntu 6.10, which I upgraded to from Ubuntu 6.02 (not a clean install of Ubuntu 6.10). I never tried to output sound through either headphone jack when I was running Ubuntu 6.02, so I don't know if this issue exists there. 

Thanks!

I can confirm that the problem where the master volume doesn't control the headphone outpout is there in Breezy, Dapper, and Edgy.  (The upgrade didn't go smoothly though).  

As for the "very low volume" from the headphone jack on the D410, I was able to adjust that.  While the master volume control doesn't change the headphone volume, there is also a setting for headphone volume and PCM volume.  Either of these volume settings should change the headphone volume.  (Some of the volume controls may not be displayed until u set the controls to display).  

However, this is not an Ubuntu specific problem.  (I've gotten tired choosing between breaking Ubuntu every six months or using old packages, so I switched to Gentoo).  In Gentoo, the master volume control in alsamixer doesn't change the headphone volume either.  

There is probably a way to work around this by assigning the volume buttons to change PCM volume, but I haven't tried that yet.

---

### Post by eggdeng on 2007-01-31
Open a terminal and type

sudo gedit /etc/modprobe.d/alsa-base

Add to end of file

```
options snd-hda-intel model=dell
```
Reboot for changes to take effect. If it doesn't work, try with
```
options snd-hda-intel model=dell-laptop
``` or
```
options snd-hda-intel model=ref
```

---

