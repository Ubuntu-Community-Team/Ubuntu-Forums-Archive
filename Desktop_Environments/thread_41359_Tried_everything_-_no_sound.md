---
title: "Tried everything - no sound"
date: 2005-06-13
forum: Desktop Environments
---

### Post by davegahan on 2005-06-13
I made a new user after GNOME crashed so badly there was no way to make it work. I transfered all settings of the old user to the new one.

Now sound does not work. 

I mades ome checks and have the following settings

peter2@ubuntulaptop:~$ lsof /dev/dsp
peter2@ubuntulaptop:~$ lsof /dev/snd/*

peter2@ubuntulaptop:~$ lsmod|grep snd
snd_intel8x0           32352  0
snd_ac97_codec         74144  1 snd_intel8x0
snd_pcm_oss            52132  0
snd_mixer_oss          19680  1 snd_pcm_oss
snd_pcm                94696  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              25060  1 snd_pcm
snd                    55012  6 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10016  1 snd
snd_page_alloc          9732  2 snd_intel8x0,snd_pcm

I cant get volume control neither : "no volune control elements and/0r devices found"
I cant get any multimedia system work "Failed to construct test pipeline for ALSA..."

What is wrong here ?

---

### Post by LaLu on 2005-06-13
what is your kernel version ?

---

### Post by davegahan on 2005-06-15
I got it solved. The issue was that the new user did not have all rights enabled - so now sound. Thank you all for the help.

---

