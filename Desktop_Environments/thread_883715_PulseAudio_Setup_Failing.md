---
title: "PulseAudio Setup Failing"
date: 2008-08-08
forum: Desktop Environments
---

### Post by flickerfly on 2008-08-08
I've been messing with pulseaudio on hardy heron for days trying to get it to work. I had it working great for about 15 minutes after logging out and back in. Then it started failing again. I've followed all the directions about redirecting stuff with aoss and pointing alsa to pulseaudio. I even setup Skype to work with it. All that stuff worked for a short period of time. I changed nothing when it broke and I have just hoped it would come back, but it hasn't. :confused:

My symptoms:
[LIST]
[*]Sound at startup, but not after
[*]Banshee won't progress a song past 0:00 and no sound is ever heard
[*]flash video pauses at ~0:02 and no sound is ever heard (I have the lib that's supposed to fix that installed)
[*]volume controls are all set appropriately
[/LIST]

What can I do to figure out this problem?

---

### Post by flickerfly on 2008-08-15
Okay, that's a pulseaudio fail then... How do I get my old stuff back?

---

### Post by leepesjee on 2008-08-16
It could also be the other way round (sound works when pulseaudio if off). The good news that all pulseaudio troubles have found solutions. There are three options. You can permanently remove pulseaudio (sounds more rigorous than it is, you really can do everything without it), see:
[http://ubuntuforums.org/showthread.php?t=885437](http://ubuntuforums.org/showthread.php?t=885437)
Or you can try to fix all the pulseaudio issues, see: 
[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)
Or you can go with jack and simply route the output of pulseaudio to jack, see:
[http://ubuntuforums.org/showthread.php?t=875378](http://ubuntuforums.org/showthread.php?t=875378)
Hope this helps, Leo.

---

### Post by leepesjee on 2008-08-16
P.S. and don't forget to vote in poll: [http://ubuntuforums.org/showthread.php?t=884750](http://ubuntuforums.org/showthread.php?t=884750)

---

### Post by flickerfly on 2008-08-16
Thanks Leepesjee, I didn't find any one link solved all my problems. I did find logging out and back in was a critical step for testing. I think I have everything working now. I hope they (the various groups responsible whomever they may be) correct this sort of stuff before the next role of Ubuntu. This was really annoying, but I learned a few things about Linux audio!

---

