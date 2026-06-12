---
title: "Lucid (10.04) No sound after upgrade from 9.10"
date: 2010-06-16
forum: Desktop Environments
---

### Post by rocsco on 2010-06-16
Once again, after upgrade - NO SOUND. 

Read all the various forum attempts at getting sound working. Tried them. Still doesn't work. Has been an ongoing problem after each release.

Pulseausdio has been removed but still seems to be there somehow, as in, when running alsamixer, the following is output:
--------------------------------
alsamixer
ALSA lib pulse.c:229:(pulse_connect) PulseAudio: Unable to connect: Connection refused

cannot open mixer: Connection refused
--------------------------------
or, aplay -l, produces:

aplay: device_list:223: no soundcards found...

so, I guess that's the problem. But how do you get it to recognise the card?

The only thing that has been done since upgrading was to remove pulseaudio which wasn't part of the prior install in anycase but somehow injected itself during the upgrade.

Hoping someone, somewhere, has the answers to this very frustrating problem.

Regards
Rosco

---

### Post by philinux on 2010-06-16
[http://ubuntuforums.org/showthread.php?t=1508909&highlight=sound](http://ubuntuforums.org/showthread.php?t=1508909&highlight=sound)

Try post #7

---

### Post by rocsco on 2010-06-16
Phil

Thank you for the pointer, but no banana, unfortunately.

Did all that, still no sound.

Some more info:

I do have a sound card as shown by **sudo lspci -v**

> 00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
	Subsystem: Giga-byte Technology Device a002
	Flags: bus master, fast devsel, latency 0, IRQ 29
	Memory at ec100000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
	Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [130] Root Complex Link <?>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

And, **aplay -l** now says I do have a sound card (that's progress), as in:
> **** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC889A Analog [ALC889A Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC889A Digital [ALC889A Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

But, **alsamixer**, still thinks PulseAudio is somehow involved (even though it has been purged), as in:
> ALSA lib pulse.c:229: (pulse_connect) PulseAudio: Unable to connect: Connection refused

cannot open mixer: Connection refused

I am really confused about what the hell has happened. Is there any way of rectifying the situation short of re-installing from scratch which would be a very large job, best avoided.

Regards
Ross

---

### Post by XubuRoxMySox on 2010-06-17
I'm using Xubuntu rather than Ubuntu, but for the first time now even Xubuntu hips with PulseAudio (grrrrr!) which has to be purged.

PulseAudio took the place of esound, as I understand it. Try opening a terminal and input

```
apt-get install esound
```

I also poked around Synaptic, looking at my *installed* software and marked anything with PulseAudio in it's name for deletion (I think there was even some gstreamer thingy that had PulseAudio as a dependency). Then please let us know if it worked! It *did* work on my Xubuntu. 

Hopefully,
Robin

---

### Post by paulfiske on 2010-06-17
I am installing all updates as requested, but recently sound seems to be absent unless I reboot. The same thing is happening with the Huawei USB dongle. Sometimes it works, sometimes it doesn't. I am a beginner as far as Linux is concerned.

---

### Post by netlord on 2010-06-17
hi

at my system it helped to remove the pulseaudio sound system

sudo apt-get remove pulseaudio

it may be help you too ;)

---

### Post by paulfiske on 2010-06-17
thanks netlord. I removed Pulse Audio and added esound. This worked!

---

