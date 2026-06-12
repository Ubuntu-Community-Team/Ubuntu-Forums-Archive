---
title: "Silly sound problems, Acer 4101WLMi"
date: 2005-12-25
forum: General Help
---

### Post by whiterussian on 2005-12-25
Hello World.

I am having all kinds of fun with my sound card, the drivers appear to be installed, and it doesnt work.

I've just installed ubuntu 5.10 breezy badger, totem tells me it cannot open the device for writing when i attempt to play a sound file, there are no login sounds, or system sounds, however if i killall aplay or killallesd, aplay will play my .wav files, however it seems to play them in super speed, fast enough that an entire song takes a couple of seconds total.

I have the same results whether the sounder server is on or off.

Here are my outputs:

$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: ICH6 [Intel ICH6], device 0: Intel ICH [Intel ICH6]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: ICH6 [Intel ICH6], device 4: Intel ICH - IEC958 [Intel ICH6 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

$ lsmod | grep snd
snd_intel8x0           30144  3
snd_ac97_codec         72188  1 snd_intel8x0
snd_pcm_oss            46368  0
snd_mixer_oss          16128  1 snd_pcm_oss
snd_pcm                78344  4 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              21764  2 snd_pcm
snd                    48644  10 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9184  1 snd
snd_page_alloc         10120  2 snd_intel8x0,snd_pcm

---

### Post by BathroomNinja on 2005-12-25
This may sound stupid or strange, but try this.

Grab the Ubuntu Live CD.  Boot up to the CD and pass: acpi=off
before it boots.  I think you press F3 (?) to pass commands at boot on the Live CD.

Do that and see if the sound works.  Please post your results.

---

### Post by whiterussian on 2005-12-25
Hey, to get ubuntu to install i had to disable acpi in the first place, as it is currently installed, any way i can turn it on or off now?

---

### Post by whiterussian on 2005-12-25
So to clarify, theres an issue with my laptop where to get a linux cd, both live or install, to boot, i have to disable acpi, and everything else then works perfectly, although i do like sound...

---

### Post by BathroomNinja on 2005-12-26
What I'm going off of, is this thread:[http://www.ubuntuforums.org/showthread.php?t=21232&highlight=Acer+4101WLMi](http://www.ubuntuforums.org/showthread.php?t=21232&highlight=Acer+4101WLMi)

Where people had some issues with their laptops including your model.  There are work arounds to turning off acpi, but I'm just trying to narrow things down.  Have you tried booting it with the Live CD like I mentioned?  If so, did sound work for you?

---

### Post by whiterussian on 2005-12-26
Not yet, its downloading as we speak, cheers.

---

### Post by whiterussian on 2005-12-26
The live CD didnt work at all, it freezes just after X starts up (not gnome yet, before the splash screen even).

I've heard people have good results with Suse 10 on my model, so I'll try that one out.

cheers

---

