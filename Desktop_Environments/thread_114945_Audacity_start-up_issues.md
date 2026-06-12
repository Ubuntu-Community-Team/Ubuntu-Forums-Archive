---
title: "Audacity start-up issues"
date: 2006-01-09
forum: Desktop Environments
---

### Post by DarrenR114 on 2006-01-09
This is a cute issue which appears to be specifically an Ubuntu desktop issue - 

I installed Audacity into Breezy Badger (5.10) using Synaptic.

It installed with no problem - however whenever I start Audacity from the menu, I get a Audio I/O layer error and cannot play or record audio.

Searching Ubuntuforums and Audacity forums - I found some info about the Audacity in the Ubuntu repository being built on OSS and the default sound architecture for Ubuntu is ALSA. I installed alsa-oss package from Ubuntu universe repository - I still get the Audio I/O layer error when starting Audacity from the menu.

I also read on the Audacity forum that Audacity expects a /dev/dsp0 device and I don't have one of those. So from the command line,  in the x-term window, I ran "AUDIODEV=/dev/dsp audacity" and Audacity ran with no problem. On a lark, I also simply tried "audacity" with no AUDIODEV definition and this too ran without problem.

When I modified the GNOME menu entry for Audacity to "run from inside terminal" I still got the same Audio I/O layer problem.

I am running everything under my regular user ID, so it is not an issue of privileges.

Any ideas?

Thanks,

Ren

---

### Post by Ampersand on 2006-01-09
Does Smeg or Alacarte (menu editors, should be in apt) have an option to run programs in the terminal? I'm not in Gnome at the moment so can't check.

---

