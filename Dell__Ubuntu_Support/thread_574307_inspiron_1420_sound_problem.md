---
title: "inspiron 1420 sound problem"
date: 2007-10-12
forum: Dell  Ubuntu Support
---

### Post by totallinuxnoob on 2007-10-12
Hey everyone, my dell 1420n with preloaded Ubuntu feisty stopped emitting sound and since I came from windows (this being my first linux experience) i'm not sure what to do...i found this fix [http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Issues/Audio_not_working_properly](http://linux.dell.com/wiki/index.php/Ubuntu_7.04/Issues/Audio_not_working_properly) but I'm not sure where to go and what to do to input that stuff (i'm really confused and would appreciate instructions step by step). Help pretty please? 


While I'm here, since Gutsy (7.10) is coming in 6 days, I would like to upgrade, but would I need to do anything specific since this computer came preloaded or could I just install from CD like normal?

---

### Post by ddrichardson on 2007-10-13
If it's stopped working, as in was working, then that guide may not help as it's designed for problems with never having had sound.

First off, check the obvious - has the sound been muted? In the system notification area (top right) what does the icon look like?

As for Gutsy, I'd habg slack for a little longer, because the version of Ubuntu 7.04 preinstalled on Dells is slightly modified from the Vanilla version to accomodate Dell laptops. Rumour has it the same will happen for 7.10

---

### Post by JangMunho on 2007-10-13
You can download alsa driver from [www.alsa-project.org](www.alsa-project.org) and compile the driver yourself. Something should be mentioned is that don't forget to add  a line which contains "options snd-hda-intel model=ref" at the end of /etc/modprobe.d/alsa-base, otherwise the driver won't work.

If you wanna update to 7.10, I don't recommend you to do so, you may be faced with a lot of problems. You'd better install it from a CD.

---

### Post by BlackRoseBud on 2007-11-05
Download and burn Ubuntu 7.10 Gutsy Gibbon.  Then do a fresh install from the cd.  It works better on the Inspiron 1420n than Fiesty, but don't try to download the updates without doing a clean install, because you'll get all kinds of errors. :(

Let me know if you need instructions on how to burn the cd or install Gutsy.

---

### Post by MikeRussell on 2007-11-05
Hi Guys,

   Quick question along the same lines...  I have the 1420 and just did a fresh install with Gutsy.  I followed the Dell wiki workaround so that sound would work on resuming from suspend and all is well.  My question lies with getting the 2nd headphone jack to output (currently only the left works).  Would installing the alsa driver from source fix this?  Last time I tried to do so, my card failed to be recognized (though I didn't add "option hda_intel_snd model=3stack").  Any help would be HUGELY appreciated.  Thanks!
Mike

---

