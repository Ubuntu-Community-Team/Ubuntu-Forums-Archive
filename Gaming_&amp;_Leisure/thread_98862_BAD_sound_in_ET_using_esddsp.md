---
title: "BAD sound in ET using esddsp"
date: 2005-12-04
forum: Gaming &amp; Leisure
---

### Post by andefeldt on 2005-12-04
Hi,

I have (as most other people) problems with the sound in ET-2.60. I use Ubuntu 5.10.

I've tried the 

killall esd
et
esd

trick, but it didn't help. I got an error about:

------- sound initialization -------
GETOSPACE: Invalid argument
Um, can't do GETOSPACE?
---------------------------------------

Haven't been able to find any solutions for this one. However, I tried using:

esddsp --mmap et

and this gave me sound in ET. The sound is, however, terrible! It's chopped into bits. Anyone with a solution for this one?

It provides me with this information:

------- sound initialization -------
------------------------------------
----- Sound Info -----
sound system is muted
    1 stereo
32768 samples
   16 samplebits
    1 submission_chunk
22050 speed
0x0x9611b48 dma buffer
No background file.
----------------------
Sound memory manager started

Anyone?

A.

---

### Post by Razvan on 2005-12-04
hi there, have a look for the names of dsp files in your /dev/directory, look for something like /dev/dsp1, /dev/dsp0, /dev/adsp or so

then see if the file that you found is also entered in /home/you/.etwolf/etmain/profiles/yourprofilename/etconfig.cfg in the line that says seta sounddevice "/dev/bla"

turn off esd before...and check if your volume is turned up

hope that helps, cheers, Martin

---

### Post by andefeldt on 2005-12-05
I checked. /dev/dsp exists. And that device is also written in the config file for ET. 

esddsp --mmap et

works, but with chopped sound. Isn't there a way to avoid this?

It would be best if I could just use the game without problems, but that doesn't seem to be the case. I had problems with bad sound in Doom3 and Quake4 also, but I just need to start those with, eg.:

quake4 +set s_driver oss

That option isn't available for ET, I guess. Isn't there something similar?

A.

---

### Post by andefeldt on 2005-12-06
I found a solution. 

sudo chmod 666 /proc/asound/card0/pcm0p/oss
sudo echo "et.x86 0 0 direct" > /proc/asound/card0/pcm0p/oss
et

Then it works perfectly! I don't even have to kill esd!

I'm just really tired of sound configurations on Linux. OSS/ALSA/ESD/ARTSD, totally confusing. Back in the good old days with only OSS, no games and no problems were showing up when you wanted to play or something. I guess that ALSA is a perfect replacement, however OSS still lives and is a lot easier to configure (plus most games just works with OSS). Maybe it's just me? And why do we suddenly need ESD and ARTSD?

Shouldn't it be possible soon to just use ALSA and nothing else?

A.

---

