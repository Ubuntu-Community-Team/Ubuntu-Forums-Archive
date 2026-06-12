---
title: "Firefox Closes Without Warning"
date: 2009-05-07
forum: Desktop Environments
---

### Post by TroyMW on 2009-05-07
I recently upgraded from 8.10 to 9.04.  Now firefox closes without warning.  When I run firefox from a terminal I get the following messages:

ALSA lib pcm_pulse.c:626:(pulse_prepare) PulseAudio: Unable to create stream: Invalid argument

E: shm.c: mmap() failed: Cannot allocate memory

firefox: pulse.c:200: pulse_new: Assertion `p->context' failed.


Any suggestions?

---

### Post by joewski on 2009-05-07
You should be on 3.0.10 of firefox. I think 9.04 came out with 3.0.8. Try updating your system.

The problem is very unusual and you may need to reinstall Firefox via the package manager.

---

### Post by TroyMW on 2009-05-16
Firefox 3.0.10 is already installed.  The error occurs when there are videos on the page or when I try to load a video from YouTube.

---

### Post by Kimm on 2009-05-16
It seems to be a PulseAudio issue, it looks like Pulse cant access the soundcard, do you have any other applications running that use sound?

Its probably a configuration issue

---

### Post by keithld on 2009-05-16
Do you have ALSA installed along with Pulse Audio?????...  You only need to be using one or the other....

If you know you have ALSA installed then remove Pulse Audio in the Synaptic Package Manager and then restart and see if that resolves the issue...

I installed ALSA because of SKYPE Issues with Pulse....

---

### Post by Kimm on 2009-05-16
> **keithld said:**
> Do you have ALSA installed along with Pulse Audio?????...  You only need to be using one or the other....

If you know you have ALSA installed then remove Pulse Audio in the Synaptic Package Manager and then restart and see if that resolves the issue...

I installed ALSA because of SKYPE Issues with Pulse....

Eh? PulseAudio uses ALSA... also, Skype works with Pulse nowadays, you just need to set it up to use it ;)

to the OP: What version of Flash are you using? I just now remembered that Flash 9 used to have issues with Pulse, if your using that you should upgrade to flash 10 (which I believe is in the repositories, as flashplugin-nonfree), there is even an alfa version of Flash 10 for 64bit which I've been using for ages without any issues what so ever (its not bundled with Ubuntu though), in case your using 64bit.

---

