---
title: "Sound Corruption"
date: 2013-07-20
forum: Desktop Environments
---

### Post by Digital Prion on 2013-07-20
Hi, thanks for having me on this forum. I spent some hours putting my well honed searchengine-fu skills to use, but haven't had much luck.

I'm having a seemingly obscure issue with audio, and would appreciate any helpful input. Sound periodically 'corrupts' and screeches, squeels, or becomes static-y. This typically occurs when I have a sound generating piece of software open, and then open a second program which generates sound. It does happen at seemingly arbitrary moments though, when the system is not in use and nothing is visibly changing.

I'm using Xubuntu 13.04 x64, fully updated. I have not installed or altered any sound software, and use Xubuntu 13.04's standard pavucontrol GUI via the panel to control sound. Under pavucontrol 'Configuration', I am using 'Analog Surround 5.1 Output' as my 'Built-In Audio' setting. 

My issue is resolved by changing the 'Built-In Audio' setting to anything else, then switching back to 'Analog Surround 5.1 Output'. The issue does eventually arise with any setting (I tried 7.1 in particular). This is tedious though, and it's very disturbing to have my music and videos interrupted by extremely loud nails-on-chalkboard screeching periodically.

Some relevant(?) system information:

Speakers: Logitech X-540 5.1 Surround ("matrix" turned off)

```

$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC892 Analog [ALC892 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 1: ALC892 Digital [ALC892 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```
Note: I don't use the Nvidia HDMI. It gets enabled each boot, then I manually disable it. Other than a minor annoyance, it doesn't seem to have any impact on my system.

```

$ lspci -v
...
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
    Subsystem: ASUSTeK Computer Inc. Device 8436
    Flags: bus master, fast devsel, latency 0, IRQ 22
    Memory at f7620000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
    Capabilities: [60] MSI: Enable- Count=1/1 Maskable- 64bit+
    Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [100] Virtual Channel
    Capabilities: [130] Root Complex Link
    Kernel driver in use: snd_hda_intel
...

```

Other than the aforementioned problem, sound seems to work flawlessly. Can't say yet whether 5.1 is actually working properly or if it's just speaker filling, but that's something to explore another day. ;)

---

