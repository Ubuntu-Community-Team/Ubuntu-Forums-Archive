---
title: "Sound Problem"
date: 2006-01-11
forum: Desktop Environments
---

### Post by c2483 on 2006-01-11
Ok
I got a bluegears xmystique 7.1 because it has an optical out so I can hook it up to my receiver.   I got some sound working by enabling iec958 output switch in the asound.state file.  Some sound works, but not all.
Login sound works
Ubuntu device database under system tools does not work
xmms works if I change the sound device in prefs
battle of wesnoth sound does not work (i did install the additional sound package)
quod libet sound does not work

is there any way to get these other programs to output some sound

---

### Post by aamehl on 2006-01-11
A few questions:
Did you go to the alsa site and check that your sound card is supported?
Did you check that modules for your sound card are loaded as root type lsmod in the terminal window.

finally did you run alsamixer and make sure that the needed channels are unmuted?

Aaron

---

### Post by c2483 on 2006-01-11
charles@charles:~$ lsmod | grep snd
snd_cmipci             35200  1
gameport               16392  1 snd_cmipci
snd_pcm_oss            51232  0
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                91020  2 snd_cmipci,snd_pcm_oss
snd_page_alloc         11408  1 snd_pcm
snd_opl3_lib           10880  1 snd_cmipci
snd_timer              24200  2 snd_pcm,snd_opl3_lib
snd_hwdep              10784  1 snd_opl3_lib
snd_mpu401_uart         7936  1 snd_cmipci
snd_rawmidi            27040  1 snd_mpu401_uart
snd_seq_device          9488  2 snd_opl3_lib,snd_rawmidi
snd                    55784  12 snd_cmipci,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_opl3_lib,snd_timer,snd_hwdep,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore              10912  1 snd

---

### Post by jerrykenny on 2006-01-11
"Some sound works, but not all."   implies the sound card is configured OK,   check your gnome desktop pregerences, and uncheck "sounds for events", also goto    preferences >  multimedia systems selector  ,  and try changing from esd to alsa on both input and output ( dont test it though . . . . this just hangs on my system )

---

