---
title: "Alsa problems in ubuntu 12.04"
date: 2012-10-20
forum: Desktop Environments
---

### Post by jambel on 2012-10-20
I just make a fresh install of ubuntu 12.04

I experience this error when i try to play sounds from different programs, it appears that can't handle sounds simultaneously:

ALSA lib pcm_dmix.c:1018 : (snd_pcm_dmix_open) unable to open slave
aplay: main:682: audio open error: Device or resource busy

any ideas?


```
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC882 Analog [ALC882 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC882 Digital [ALC882 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
``````
aplay -L
default
    Playback/recording through the PulseAudio sound server
sysdefault:CARD=Intel
    HDA Intel, ALC882 Analog
    Default Audio Device
front:CARD=Intel,DEV=0
    HDA Intel, ALC882 Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, ALC882 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, ALC882 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, ALC882 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, ALC882 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, ALC882 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Intel,DEV=0
    HDA Intel, ALC882 Digital
    IEC958 (S/PDIF) Digital Audio Output
dmix:CARD=Intel,DEV=0
    HDA Intel, ALC882 Analog
    Direct sample mixing device
dmix:CARD=Intel,DEV=1
    HDA Intel, ALC882 Digital
    Direct sample mixing device
dsnoop:CARD=Intel,DEV=0
    HDA Intel, ALC882 Analog
    Direct sample snooping device
dsnoop:CARD=Intel,DEV=1
    HDA Intel, ALC882 Digital
    Direct sample snooping device
hw:CARD=Intel,DEV=0
    HDA Intel, ALC882 Analog
    Direct hardware device without any conversions
hw:CARD=Intel,DEV=1
    HDA Intel, ALC882 Digital
    Direct hardware device without any conversions
plughw:CARD=Intel,DEV=0
    HDA Intel, ALC882 Analog
    Hardware device with all software conversions
plughw:CARD=Intel,DEV=1
    HDA Intel, ALC882 Digital
    Hardware device with all software conversions

```

---

### Post by jambel on 2012-10-21
bump

---

