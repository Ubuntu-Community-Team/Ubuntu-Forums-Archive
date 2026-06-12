---
title: "XBMC had no HDMI sound"
date: 2012-04-10
forum: Desktop Environments
---

### Post by Lemuriano on 2012-04-10
Hi,

I just assemble an HTPC (Asus AT510NT-I Intel Atom D525 (1.8ghz dual core) BGA 559 Intel NM10 Mini ITX motherboard with 4g of DDR3 800 ram). The pc is running Xubuntu 12.04 with and I install the proprietary drivers.

The problem is that while the system have sound through HDMI and I can enjoy movies with Parole or VLC and listen to music, the sound is no where to be found when using XBMC Eden. 

If I install XBMC with Ubuntu the sound is fine and if I sudo apt-get install xubuntu-desktop on the Ubuntu install the sound is there too. 

The sound settings on the XBMC with Xubuntu-desktop are:

1- Audio output = Analog
2-    ¨           ¨        = default

But these setting don´t work if I install just Xubuntu alone.

Most of the time solutions are easy. The difficult part is finding then.

Thanks

---

### Post by papibe on 2012-04-10
Hi Lemuriano.

I imagine the proprietary driver you installed is the Nvidia driver right?

Could you post the result of this command?
```
aplay -L
```
Regards.

---

### Post by Lemuriano on 2012-04-11
Thanks for your interest and yes, the drivers are Nvidia. 

[HTML]htpc@Blackbox:~$ aplay -L
default
    Playback/recording through the PulseAudio sound server
sysdefault:CARD=Intel
    HDA Intel, ALC887 Analog
    Default Audio Device
front:CARD=Intel,DEV=0
    HDA Intel, ALC887 Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, ALC887 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, ALC887 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, ALC887 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, ALC887 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, ALC887 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Intel,DEV=0
    HDA Intel, ALC887 Digital
    IEC958 (S/PDIF) Digital Audio Output
dmix:CARD=Intel,DEV=0
    HDA Intel, ALC887 Analog
    Direct sample mixing device
dmix:CARD=Intel,DEV=1
    HDA Intel, ALC887 Digital
    Direct sample mixing device
dsnoop:CARD=Intel,DEV=0
    HDA Intel, ALC887 Analog
    Direct sample snooping device
dsnoop:CARD=Intel,DEV=1
    HDA Intel, ALC887 Digital
    Direct sample snooping device
hw:CARD=Intel,DEV=0
    HDA Intel, ALC887 Analog
    Direct hardware device without any conversions
hw:CARD=Intel,DEV=1
    HDA Intel, ALC887 Digital
    Direct hardware device without any conversions
plughw:CARD=Intel,DEV=0
    HDA Intel, ALC887 Analog
    Hardware device with all software conversions
plughw:CARD=Intel,DEV=1
    HDA Intel, ALC887 Digital
    Hardware device with all software conversions
hdmi:CARD=NVidia,DEV=0
    HDA NVidia, HDMI 0
    HDMI Audio Output
hdmi:CARD=NVidia,DEV=1
    HDA NVidia, HDMI 0
    HDMI Audio Output
hdmi:CARD=NVidia,DEV=2
    HDA NVidia, HDMI 0
    HDMI Audio Output
hdmi:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    HDMI Audio Output
dmix:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    Direct sample mixing device
dmix:CARD=NVidia,DEV=7
    HDA NVidia, HDMI 0
    Direct sample mixing device
dmix:CARD=NVidia,DEV=8
    HDA NVidia, HDMI 0
    Direct sample mixing device
dmix:CARD=NVidia,DEV=9
    HDA NVidia, HDMI 0
    Direct sample mixing device
dsnoop:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    Direct sample snooping device
dsnoop:CARD=NVidia,DEV=7
    HDA NVidia, HDMI 0
    Direct sample snooping device
dsnoop:CARD=NVidia,DEV=8
    HDA NVidia, HDMI 0
    Direct sample snooping device
dsnoop:CARD=NVidia,DEV=9
    HDA NVidia, HDMI 0
    Direct sample snooping device
hw:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    Direct hardware device without any conversions
hw:CARD=NVidia,DEV=7
    HDA NVidia, HDMI 0
    Direct hardware device without any conversions
hw:CARD=NVidia,DEV=8
    HDA NVidia, HDMI 0
    Direct hardware device without any conversions
hw:CARD=NVidia,DEV=9
    HDA NVidia, HDMI 0
    Direct hardware device without any conversions
plughw:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    Hardware device with all software conversions
plughw:CARD=NVidia,DEV=7
    HDA NVidia, HDMI 0
    Hardware device with all software conversions
plughw:CARD=NVidia,DEV=8
    HDA NVidia, HDMI 0
    Hardware device with all software conversions
plughw:CARD=NVidia,DEV=9
    HDA NVidia, HDMI 0
    Hardware device with all software conversions
[/HTML]

---

### Post by papibe on 2012-04-11
This is how I do it on my laptop with an Nvidia card:

I set directly the output to the alsa driver on XBMC:
```

System -> Settings:

    Audio Output                           HDMI
    Speaker Configuration                  2 *

    Boost volume on downmix                Enabled.
    - Dolby Digital (AC3) capable receiver Disable.
    - DTS  capable receiver                Disable.

    Audio output device                    Custom
    Custom audio device                    hw:1,9

    Passthrough output device              Custom
    Custom passthrough device              hw:1,9
```
(* because my Nvidia card only supports stereo).

From your aplay output I see that you have several Nvidia HDMI output devices. I would try them all:
```
hw:1,3
hw:1,7
hw:1,8
hw:1,9
```
I hope that helps, and tell us how it goes.
Regards.

---

### Post by Lemuriano on 2012-04-11
Hi papibe,

I´m grateful for your assistance. XBMC sounds laud and clear.:popcorn:

```
hw:1,7
```

This was the winning combination!

Seen the power of the collaborative effort that come from the community make me feel humble.

Thanks

---

### Post by wiz561 on 2012-04-30
Wanted to say thank you too.  The hw:1,7 worked for me as well.  You prevented me from pulling more hair out!

---

### Post by matthewcb on 2012-10-14
I know it's very late to this thread, but found this when searching for a fix for my own sound issues and it worked a treat.

Just wanted to post a thank you :)

---

### Post by christiansenk on 2013-01-19
Many thanks.

Tried all issues and don't have a very complicated setup or needs.

The final solution after trying most was to disable the navigation sounds!


Simple solution if you don't mind not having the menu sounds turned on:

[http://forums.whirlpool.net.au/archive/1897593](http://forums.whirlpool.net.au/archive/1897593)

---

