---
title: "htpc ubuntu 12.10 + xbmc 11 = no sound via hdmi"
date: 2012-11-20
forum: Desktop Environments
---

### Post by Chrissii on 2012-11-20
Hey guys,

I have a little problem. I did a lot of research in advance, read a lot of threads on ubuntuforums.org and stuff but I could not figure out how to solve my sound problem at all..
I would be glad if someone would be interested in helping me out, I would really appreciate it

my problem: I dont get any sound out of my ubuntu 12.10 installation in combination with xbmc11 Eden. I only have/use a hdmi cable to my tv

my hardware: 
i3 3225 (HD 4000)
B75 Pro3-M
the soundchip is a Realtek ALC892 in combination with HDA intel PCH

here is my aplay -l output:
(sorry its in german, hope you understand it anyway...)

> **** Liste der Hardware-Geräte (PLAYBACK) ****
Karte 0: PCH [HDA Intel PCH], Gerät 0: ALC892 Analog [ALC892 Analog]
  Sub-Geräte: 0/1
  Sub-Gerät #0: subdevice #0
Karte 0: PCH [HDA Intel PCH], Gerät 1: ALC892 Digital [ALC892 Digital]
  Sub-Geräte: 1/1
  Sub-Gerät #0: subdevice #0
Karte 0: PCH [HDA Intel PCH], Gerät 3: HDMI 0 [HDMI 0]
  Sub-Geräte: 1/1
  Sub-Gerät #0: subdevice #0
Karte 0: PCH [HDA Intel PCH], Gerät 7: HDMI 1 [HDMI 1]
  Sub-Geräte: 1/1
  Sub-Gerät #0: subdevice #0
Karte 0: PCH [HDA Intel PCH], Gerät 8: HDMI 2 [HDMI 2]
  Sub-Geräte: 1/1
  Sub-Gerät #0: subdevice #0


and my aplay -L output:

> null
    Discard all samples (playback) or generate zero samples (capture)
pulse
    PulseAudio Sound Server
default:CARD=PCH
    HDA Intel PCH, ALC892 Analog
    Default Audio Device
sysdefault:CARD=PCH
    HDA Intel PCH, ALC892 Analog
    Default Audio Device
front:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    Front speakers
surround40:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Digital
    IEC958 (S/PDIF) Digital Audio Output
hdmi:CARD=PCH,DEV=0
    HDA Intel PCH, HDMI 0
    HDMI Audio Output
hdmi:CARD=PCH,DEV=1
    HDA Intel PCH, HDMI 1
    HDMI Audio Output
hdmi:CARD=PCH,DEV=2
    HDA Intel PCH, HDMI 2
    HDMI Audio Output
dmix:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    Direct sample mixing device
dmix:CARD=PCH,DEV=1
    HDA Intel PCH, ALC892 Digital
    Direct sample mixing device
dmix:CARD=PCH,DEV=3
    HDA Intel PCH, HDMI 0
    Direct sample mixing device
dmix:CARD=PCH,DEV=7
    HDA Intel PCH, HDMI 1
    Direct sample mixing device
dmix:CARD=PCH,DEV=8
    HDA Intel PCH, HDMI 2
    Direct sample mixing device
dsnoop:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    Direct sample snooping device
dsnoop:CARD=PCH,DEV=1
    HDA Intel PCH, ALC892 Digital
    Direct sample snooping device
dsnoop:CARD=PCH,DEV=3
    HDA Intel PCH, HDMI 0
    Direct sample snooping device
dsnoop:CARD=PCH,DEV=7
    HDA Intel PCH, HDMI 1
    Direct sample snooping device
dsnoop:CARD=PCH,DEV=8
    HDA Intel PCH, HDMI 2
    Direct sample snooping device
hw:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    Direct hardware device without any conversions
hw:CARD=PCH,DEV=1
    HDA Intel PCH, ALC892 Digital
    Direct hardware device without any conversions
hw:CARD=PCH,DEV=3
    HDA Intel PCH, HDMI 0
    Direct hardware device without any conversions
hw:CARD=PCH,DEV=7
    HDA Intel PCH, HDMI 1
    Direct hardware device without any conversions
hw:CARD=PCH,DEV=8
    HDA Intel PCH, HDMI 2
    Direct hardware device without any conversions
plughw:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    Hardware device with all software conversions
plughw:CARD=PCH,DEV=1
    HDA Intel PCH, ALC892 Digital
    Hardware device with all software conversions
plughw:CARD=PCH,DEV=3
    HDA Intel PCH, HDMI 0
    Hardware device with all software conversions
plughw:CARD=PCH,DEV=7
    HDA Intel PCH, HDMI 1
    Hardware device with all software conversions
plughw:CARD=PCH,DEV=8
    HDA Intel PCH, HDMI 2
    Hardware device with all software conversions


lspci -v shows the following about my audio device:
> 00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
        Subsystem: ASRock Incorporation Device 8892
        Flags: bus master, fast devsel, latency 0, IRQ 49
        Memory at f7d10000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: snd_hda_intel
        Kernel modules: snd-hda-intel


you can also see that xbmc is using the sound device:
> 
"lsof | grep snd"
 272519 /usr/lib/x86_64-linux-gnu/libsndfile.so.1.0.25
xbmc.bin   5009  5078 mediaserver   53r      CHR             116,33      0t0       1493 /dev/snd/timer
xbmc.bin   5009  5078 mediaserver   54u      CHR              116,7      0t0       9804 /dev/snd/pcmC0D0p
xbmc.bin   5009  5078 mediaserver   55u      CHR             116,11      0t0       9808 /dev/snd/controlC0
xbmc.bin   5009  5079 mediaserver  mem       CHR              116,7                9804 /dev/snd/pcmC0D0p
xbmc.bin   5009  5079 mediaserver  mem       REG                8,1   401440

Also it is possible to play files via aplay. nevertheless I cant hear any sounds...
> :~$ aplay /usr/share/sounds/alsa/Front_Center.wav
Wiedergabe: WAVE '/usr/share/sounds/alsa/Front_Center.wav' : Signed 16 bit Little Endian, Rate: 48000 Hz, mono

its also possible to run "speaker-test" without any errors..

this is what I already tried: 

- I tried almost every combination of xbmc settings to get any kind of sound. I already set it to custom and used hw:0,3/7/8, hdmi:0,0/1/2 . same with plughw: and dmix:

- already uninstalled pulseaudio via apt-get purge pulseaudio, because a lot of people are describing errors with pulseaudio and xbmc (but its still showing up on aplay -L)

- also used alsamixer to unmute my sound device. alsamixer is also showing up the Intel PCH as audiodevice being in use.
Nevertheless I cant get any audio. the settings->audio preferences dont show any possible devices (I dont get that)

- did 
> add-apt-repository ppa:team-iquik/alsa
add-apt-repository ppa:ubuntu-audio-dev/ppa
apt-get update
apt-get upgrade

found on the xbmc wiki page

- I installed the newest realtek audiopack via the ./install script in the package. 

sorry for this spam, but i thought it would be good to deliver all the informations at once..

so does somebody feel like he could help me? 
thanks in advance !

EDIT 22.11.2012:

k I did a reinstall of alsa-base/alsa-utils, pulseaudio and gstreamer + a kernel reinstall from kernel.ubuntu.com and now I can get at least sound over the 3,5mm jack. Still cant get sound over hdmi and no sound over the settings->audio tab. Aplay and even xbmc is working fine over 3,5mm. 
Does somebody have a clue what could be wrong with my hdmi output?
its not the tv and it is not the hardware. Hdmi soundoutput is working on other distributions..

EDIT 22.11.2012

Job done. Dont know how, dont know why. I believe it was alsa. just uninstalled and removed every single file used by alsa/gstreamer/pulseaudio I could. Just reinstalled alsa again. after unmuting the alsamixer again and trying some settings in xbmc (hdmi - custom hw:0,8 - custom hw:0,8 is the working one) suddenly some sound came out of my tv.

---

