---
title: "Strange alsa behaviour - either no sound or no mic? Suggestions?"
date: 2012-10-18
forum: Desktop Environments
---

### Post by latebeat on 2012-10-18
Hi all,

I'm having such a hard time with audio problems on my laptop. I've spent days researching and googling but still to this day I haven't found a 100% working solution.
I have a sony vaio z1 (vpc-z) laptop with the following:

[LIST]
[*]internal speakers
[*]internal mic
[*]front headphones port
[*]front headphones port mic (for headphones with integrated mic)
[*]front mic port
[/LIST]
So with an out of the box install I have no sound from the internal speakers but all the rest is working fine.


**So default install:**
internal speakers not working - rest is working

*[I]_now if I modify /etc/modprobe.d/alsa-base.conf _*[/I]
and add the following line: **options snd-hda-intel model=auto**
internal speakers not working - all the rest working (same behaviour as before)

if I modify /etc/modprobe.d/alsa-base.conf 
and add the following line **options snd-hda-intel model=sony-vaio-tt**
internal speakers do work, however internal mic is not working!
:guitar:

I'm on kubuntu 12.04 and I'm using the ppa for the latest alsa builds. Also I've tried the hda-sound-retasker little app and tried to override either the internal speakers or the mic with no result.

I've run out of ideas at this point and I'm really tired of rebooting my laptop :confused:

So far, when I need to use my mic I reboot with B]options snd-hda-intel model=sony-vaio-tt[/B] while when I need to watch a movie I reboot with B]options snd-hda-intel model=options[/B]. 

any ideas or suggestions?

---

