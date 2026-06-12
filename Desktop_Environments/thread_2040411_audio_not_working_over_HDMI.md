---
title: "audio not working over HDMI"
date: 2012-08-11
forum: Desktop Environments
---

### Post by adleong on 2012-08-11
Hi,

I've just set up Ubuntu running on what I hope to be a media computer.  Video over HDMI works fine but audio does not.  I'm using the onboard HDMI port on a Asus F1A75-M motherboard.  HDMI doesn't show up as an option in System Settings -> Sound.

Here is the output of aplay -l
```
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Generic [HD-Audio Generic], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Generic_1 [HD-Audio Generic], device 0: VT1708S Analog [VT1708S Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Generic_1 [HD-Audio Generic], device 1: VT1708S Digital [VT1708S Digital]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: Generic_1 [HD-Audio Generic], device 2: VT1708S HP [VT1708S HP]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Any advice would be greatly appreciated!  Thanks!

---

