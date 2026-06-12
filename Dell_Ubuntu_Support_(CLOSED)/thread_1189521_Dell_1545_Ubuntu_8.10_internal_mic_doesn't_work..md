---
title: "Dell 1545 Ubuntu 8.10 internal mic doesn't work."
date: 2009-06-16
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Onyxrune on 2009-06-16
I just got a brand new Dell 1545 Ubuntu 8.10, but the internal mic isn't working.  Any suggestions or help?

Thank you!
Onyxrune

---

### Post by superm1 on 2009-06-17
You probably just need to set the mixer to use the digital mic by default.  Open up the mixer applet and enable all the advanced options.  Digital Input source is what you're looking for.

---

### Post by kalos on 2009-07-26
Thanks!

I was only using alsamixer in Terminal and didn't have any luck (Ubuntu 9.04). For some reason, I wasn't able to unmute my Capture.

Exact steps for anyone else: 
[LIST=1]
[*]Goto mixer applet (volume control in top panel)
[*]Left click and select Volume Control
[*]Click Preferences and enable "Capture" and "Capture 1"
[*]Switch to Recording tab and unmute "Capture" and "Capture 1"
[*]Now alsamixer shows some red stuff and "L R" around the bottom of Capture.
[/LIST]


Oh, and I also added 
```
options snd-hda-intel model=auto
```
 to my /etc/modprobe.d/alsa-base.conf but I'm not sure if that was necessary.

---

