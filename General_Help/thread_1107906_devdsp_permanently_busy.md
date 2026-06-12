---
title: "/dev/dsp permanently busy"
date: 2009-03-27
forum: General Help
---

### Post by kunami on 2009-03-27
Hi. 

I'm trying to get Mednafen to run with sound, but I can't, even on a freshly started computer (no other apps running). All other apps deal with sound just fine, the only one that doesn't is Mednafen, which says
>  Using "ALSA" audio driver with device "default":ALSA Error: snd_pcm_open(&alsa_pcm, id ? id : "hw:0", SND_PCM_STREAM_PLAYBACK, 0) Device or resource busy.

Also, "cat /dev/random > /dev/dsp" says the same thing, instead of producing the expected white noise.

The only workaround I've found that works so far, is dropping from the gdm login prompt to the console, doing a "cat /dev/random > /dev/dsp"  (which, oddly, doesn't produce any sound at all, but it doesn't give the error message either), then dropping back to gdm, logging in, then drop back to the console and killing cat. I've tried disabling GNOME login sound from starting with my gnome session, but it also didn't work.

Any ideas on what might be the problem or any solution?

EDIT: Forgot to say that I'm using 8.10.

---

### Post by kunami on 2009-03-28
Anyone?

---

