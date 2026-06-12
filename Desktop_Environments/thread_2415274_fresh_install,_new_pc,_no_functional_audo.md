---
title: "fresh install, new pc, no functional audo"
date: 2019-03-23
forum: Desktop Environments
---

### Post by derekcentrico on 2019-03-23
New ASUS Zen AiO PC here.  Old one was...old...so I upgraded.  This time around it has been a real pain trying to solve issues to get Ubuntu up and running.

Google has not been my friend for the audio matter.

```
# cat /proc/asound/card0/codec* | grep Codec
Codec: Realtek ALC274
Codec: Intel Kabylake HDMI

# cat /proc/asound/card0/pcm0c/info
card: 0
device: 0
subdevice: 0
stream: CAPTURE
id: ALC274 Analog
name: ALC274 Analog
subname: subdevice #0
class: 0
subclass: 0
subdevices_count: 1
subdevices_avail: 0

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC274 Analog [ALC274 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 9: HDMI 3 [HDMI 3]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 10: HDMI 4 [HDMI 4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

d# hwinfo --sound
21: PCI 1f.3: 0403 Audio device                                 
  [Created at pci.378]
  Unique ID: nS1_.WnojYJLVCm0
  SysFS ID: /devices/pci0000:00/0000:00:1f.3
  SysFS BusID: 0000:00:1f.3
  Hardware Class: sound
  Model: "Intel Audio device"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0xa348 
  SubVendor: pci 0x1043 "ASUSTeK Computer Inc."
  SubDevice: pci 0x31d0 
  Revision: 0x10
  Driver: "snd_hda_intel"
  Driver Modules: "snd_hda_intel"
  Memory Range: 0xdd398000-0xdd39bfff (rw,non-prefetchable)
  Memory Range: 0xdd100000-0xdd1fffff (rw,non-prefetchable)
  IRQ: 145 (663 events)
  Module Alias: "pci:v00008086d0000A348sv00001043sd000031D0bc04sc03i80"
  Driver Info #0:
    Driver Status: snd_hda_intel is active
    Driver Activation Cmd: "modprobe snd_hda_intel"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

```

Made a Youtube video of the crazy noise that happens 50% of the time.  [https://youtu.be/MUD_-Ot_IkY](https://youtu.be/MUD_-Ot_IkY)  Other 50% is no noise/audio whatsoever.  Yes, this video is from installation but it occurs the same with the fresh install up and running.

I don't see any codecs to use which match the above card....  [COLOR=#333333][FONT=UbuntuMono]/usr/share/doc/alsa-base/driver/ALSA-Configuration.txt.gz
[/FONT][/COLOR]
Very much at a loss.  Any advice appreciated.[COLOR=#333333][FONT=UbuntuMono]
[/FONT][/COLOR]

---

