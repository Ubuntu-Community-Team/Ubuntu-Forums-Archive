---
title: "Sound problem"
date: 2015-07-03
forum: Desktop Environments
---

### Post by houshdaran on 2015-07-03
Hello.
My sound doesn't work under my Ubuntu 14.04 LTS  and don't know how to troubleshoot it.

 I am running a dual-boot system of winXP & Ubuntu 14.04.

---

### Post by tgalati4 on 2015-07-03
Open a terminal and post the output of:

```
aplay -l
```

---

### Post by houshdaran on 2015-07-03
soheil@soheil-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
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
soheil@soheil-desktop:~$

---

### Post by houshdaran on 2015-07-07
Hello?! That was the display of my terminal.

---

