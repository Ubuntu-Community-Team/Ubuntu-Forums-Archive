---
title: "Dell XPS 1645 Getting HDMI Output Digital not stero?"
date: 2011-03-04
forum: Dell Ubuntu Support (CLOSED)
---

### Post by kanazky on 2011-03-04
Graphics Card:
HD 5730 ATI

Type:
Notbook XPS 1645 Dell

Source:
Any Media Source, BluRay 5.1 AC3 and DTS Audio Encoded;

Output Attempt:
HDMI to 5.1 Receiver.

aplay -l
> 
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 1: Generic [HD-Audio Generic], device 3: ATI HDMI [ATI HDMI]
Subdevices: 1/1
Subdevice #0: subdevice #0 

aplay -L
> 
null
    Discard all samples (playback) or generate zero samples (capture)
pulse
    Playback/recording through the PulseAudio sound server
front:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
dmix:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    Direct sample mixing device
dsnoop:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    Direct sample snooping device
hw:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    Direct hardware device without any conversions
plughw:CARD=Intel,DEV=0
    HDA Intel, STAC92xx Analog
    Hardware device with all software conversions
hdmi:CARD=Generic,DEV=0
    HD-Audio Generic, ATI HDMI
    HDMI Audio Output
dmix:CARD=Generic,DEV=3
    HD-Audio Generic, ATI HDMI
    Direct sample mixing device
dsnoop:CARD=Generic,DEV=3
    HD-Audio Generic, ATI HDMI
    Direct sample snooping device
hw:CARD=Generic,DEV=3
    HD-Audio Generic, ATI HDMI
    Direct hardware device without any conversions
plughw:CARD=Generic,DEV=3
    HD-Audio Generic, ATI HDMI
    Hardware device with all software conversions


Right now using asound.rc I can get some PCM 44hz to my 5.1 but that sound quality is Stereo and Low Quailty. I know from windows that I can out DTS and 5.1 Audio signals that work perfect on my 5.1 Receiver. 

Otherwise the HDMI goes fine into receiver, show up on TV and can play 44Hz Stereo sound.

How do I change it from low quality stereo to hi-quality surround?
I also want it to work with rythmbox and banshee and those kind of applications so changing vlc to alsa and spdif isn't going to be the fix I need.

---

