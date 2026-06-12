---
title: "pSX Emulator Help"
date: 2009-04-03
forum: Gaming &amp; Leisure
---

### Post by Jman1989 on 2009-04-03
I should start of by saying, I am a COMPLETE NEWBIE when it comes to Ubuntu linux. I am having a bit of a problem with the pSX emulator. When I load the bios and click ok, it just crashes. The emulator window never comes up. I ran it in the terminal and it said this

ALSA lib pulse.c:272:(pulse_connect) PulseAudio: Unable to connect: Connection refused

[src/linux/sound.cpp, line 582]: 'snd_pcm_open(&pcm_handle,dev->info->device_fname,SND_PCM_STREAM_PLAYBACK,0)' returned 'Connection refused'

(pSX:21967): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(pSX:21967): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(pSX:21967): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(pSX:21967): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(pSX:21967): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(pSX:21967): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(pSX:21967): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(pSX:21967): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
pSX: pcm_params.c:2259: snd_pcm_hw_refine: Assertion `pcm && params' failed.
Aborted

Any know how to solve the problem? I am running Ubuntu 8.10. Please help if you can!

---

### Post by Tobi-fp on 2009-04-03
It seams that your sound card is busy and clocking up..
This should be easy..try restarting your system, then run it as the first thing you do, dont open anything using your sound card..
Also, in the PSx emulator, try setting your sound config differently...

---

### Post by Tobi-fp on 2009-04-03
also try to install the glibc with
sudo apt-get install glibc

---

### Post by Jman1989 on 2009-04-03
I restarted and I just tried to install glibc and it said Couldn't find package. Also I put pSX into the terminal again and it gave me a different error this time. Now it says


(pSX:6134): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(pSX:6134): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(pSX:6134): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(pSX:6134): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(pSX:6134): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(pSX:6134): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(pSX:6134): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(pSX:6134): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(pSX:6134): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(pSX:6134): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(pSX:6134): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(pSX:6134): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(pSX:6134): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(pSX:6134): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(pSX:6134): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(pSX:6134): GLib-GObject-CRITICAL **: g_signal_handler_disconnect: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
[src/linux/sound.cpp, line 215]: 'snd_pcm_hw_params_set_access(pcm_handle,hwparams,SND_PCM_ACCESS_MMAP_INTERLEAVED)' returned 'Invalid argument'
pad=0
Segmentation fault

Im so confused x_x

---

### Post by Grishka on 2009-04-03
do 'killall pulseaudio', before running psx.

---

### Post by Jman1989 on 2009-04-04
Just did killall pulseaudio and it still will not load up.

---

### Post by dfreer on 2009-04-04
> **Jman1989 said:**
> Just did killall pulseaudio and it still will not load up.

I believe you need root permission to kill pulseaudio, been awhile since I ran Ubuntu. Try sudo killall pulseaudio, then check your running processes with gnome-system-monitor and make sure it is no longer running before starting pSX.

There are a couple scripts that have been created to kill pulseaudio, launch pSX, then restart pulseaudio when you are done playing. My (rather long) pSX thread should have a couple in it.

As for those GLib errors, they are safe to ignore. Installing libgtkglext1-dev should get rid of them anyways.

---

