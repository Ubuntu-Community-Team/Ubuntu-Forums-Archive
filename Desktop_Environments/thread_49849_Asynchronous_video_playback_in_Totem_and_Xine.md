---
title: "Asynchronous video playback in Totem and Xine"
date: 2005-07-18
forum: Desktop Environments
---

### Post by andrewleepaul on 2005-07-18
I recently switched from Fedora Core 3 to Ubuntu 5.04 (mainly due to the great packed management in Ubuntu). However, I am having the following problem with the sound.

When watching movies (DVDs, DVDs from hard disk, AVI (DivX or Xvid)) the sound becomes asynchronous after around five minutes. For the first five minutes, sound and video are perfectly synchronous. I experience the same behavior when the movie's sound is encoded in Mp3 or AC3.

I can reproduce this in Totem and Xine.

I can temporarily fix the problem by pausing and unpausing the movie. Then the sound and video become synchronous again. However, after around three to five minutes, they become asynchronous. :-(

I did not have this problem with Fedora Core 3 using the same hardware.

I have also noted that when I adjust the volume in Beep Media Player there is a short (maybe 0.75s) delay between moving the volume slider bar and the volume actually changing. Maybe this is related to the above described symptoms.

Has anyone else experienced this behavior? And does anyone have a solution?

TIA

Andrew



My hardware is this:

- CPU Intel Pentium 4 3.0GHz Box 800MHz Prescott 1024K
- MBP Asus P4P800 E Deluxe i865PE S478
- SPE 512MB TwinMos Twister CL2.0 PC400


And on the software side:

root@screwdriver:~# /sbin/lspci | grep audio
bash: /sbin/lspci: No such file or directory

---

root@screwdriver:~# lspci | grep audio
0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
root@screwdriver:~# /sbin/lsmod | grep snd
snd_intel8x0           29984  2
snd_ac97_codec         64608  1 snd_intel8x0
snd_pcm_oss            47652  1
snd_mixer_oss          16768  2 snd_pcm_oss
snd_pcm                84872  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              23300  1 snd_pcm
snd                    50276  6 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timersoundcore               9824  3 snd
snd_page_alloc          9604  2 snd_intel8x0,snd_pcm

---

root@screwdriver:~# cat /proc/asound/cards
0 [I82801DBICH4   ]: ICH4 - Intel 82801DB-ICH4
                     Intel 82801DB-ICH4 with STAC9750/51 at 0xe9101000, irq 17

---

root@screwdriver:~# cat /proc/asound/devices
  0: [0- 0]: ctl
 20: [0- 4]: digital audio playback
 27: [0- 3]: digital audio capture
 26: [0- 2]: digital audio capture
 25: [0- 1]: digital audio capture
 16: [0- 0]: digital audio playback
 24: [0- 0]: digital audio capture
 33:       : timer

---

