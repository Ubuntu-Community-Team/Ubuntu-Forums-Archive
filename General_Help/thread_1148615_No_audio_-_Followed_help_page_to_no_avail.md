---
title: "No audio - Followed help page to no avail"
date: 2009-05-04
forum: General Help
---

### Post by ashcarr on 2009-05-04
Hello.

Everything in ubuntu is working great except from the audio. Simply, there isn't any.

I've followed [this help page]("http://ubuntuforums.org/showthread.php?t=205449") to no avail and now have a 'fresh audio kernel' ready to try again.

lspci -v:
```
00:09.0 Audio device: nVidia Corporation MCP73 High Definition Audio (rev a1)
    Subsystem: Biostar Microtech Int'l Corp Device 820f
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
    Memory at efff4000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

```cat:
```
 0 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xefff4000 irq 23

```aplay -l
```
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC662 Analog [ALC662 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC662 Digital [ALC662 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```I've added my username to groups. Changed from: 
```
audio:x:29:pulse
```
to
```
audio:x:29:ash
``` I've added "snd-hda-intel" to /etc/modules
Everything in alsamixer is unmuted and at full.
And yes, the sound system is on and plugged in :)

Thank you for your time.

---

### Post by ashcarr on 2009-05-06
I just had a thought but I can't test it as I'm not at home right now.

My motherboard has a socket for the front audio ports, which is plugged in, but they have never worked. Could this be affecting it? When I get back, I will check if its routing through the front one, and if not I will disconnect it and try again.

Will Ubuntu recognize that it is no longer plugged in or will I have to change some configurations?

EDIT:
The audio is coming out of the front jack which I can live with. Autodetect crates an aweful sound as did selecting ALSA, but upon closing and reopening preferences, testing it on ALSA makes the sine wave. Problem solved it seems! Funny, Windows NEVER used the front audio even when it was plugged in, Ubuntu is the other way round!

---

