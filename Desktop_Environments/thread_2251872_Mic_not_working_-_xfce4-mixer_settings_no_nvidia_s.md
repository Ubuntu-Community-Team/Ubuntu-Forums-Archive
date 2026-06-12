---
title: "Mic not working - xfce4-mixer settings: no nvidia sound device."
date: 2014-11-07
forum: Desktop Environments
---

### Post by Jacob72 on 2014-11-07
[SIZE=2][COLOR=#333333] Since installing Xubuntu 14.04 and 14.10 on my Laptop and Desktop installations the microphone has not worked on either device. This is a system wide issue not confined to SKYPE.
[/COLOR]
[FONT=arial]**[COLOR=#333333]Testing I have p[/COLOR]**[/FONT][/SIZE][FONT=arial]**[COLOR=#333333]erformed thus far[/COLOR]**[/FONT][SIZE=2][B][COLOR=#333333][FONT=UbuntuRegular]
[/FONT][/COLOR][/B][/SIZE]

[LIST]
[*]Volume control
Not muted.
[*]Skype
Unselected 'Allow Skype to automatically adjust mixer levels'.
[*]~$ arecord -d 10 /tmp/test-mic.wav
Plays back interference noise only.
[/LIST]

**Add additional drivers**


[LIST]
[*]Installed latest driver for my Nvidia graphics card
[*]Confirmed that drivers are in use: '~$ lspci -vnn | grep -i VGA -A 12'
[/LIST]
         Kernel driver in use: nvidia

[LIST]
[*]Checked hardware acceleration
[/LIST]
         Quadro FX 1700/PCIe/SSE2
[B]
Alsamixer testing does not find nvidia sound device

[/B]
[LIST]
[*]~$ sudo aplay -l
**** List of PLAYBACK Hardware Devices ****card 0: MID [HDA Intel MID], device 0: CX20585 Analog [CX20585 Analog]Subdevices: 0/1Subdevice #0: subdevice #0card 0: MID [HDA Intel MID], device 3: HDMI 0 [HDMI 0]Subdevices: 1/1Subdevice #0: subdevice #0
[/LIST]

[LIST]
[*]~$ aplay -lL
[/LIST]
[FONT=Ubuntu Mono]default    Playback/recording through the PulseAudio sound servernull    Discard all samples (playback) or generate zero samples (capture)pulse    PulseAudio Sound Serversysdefault:CARD=Intel    HDA Intel, AD1988 Analog    Default Audio Devicefront:CARD=Intel,DEV=0    HDA Intel, AD1988 Analog    Front speakerssurround40:CARD=Intel,DEV=0    HDA Intel, AD1988 Analog    4.0 Surround output to Front and Rear speakerssurround41:CARD=Intel,DEV=0    HDA Intel, AD1988 Analog    4.1 Surround output to Front, Rear and Subwoofer speakerssurround50:CARD=Intel,DEV=0    HDA Intel, AD1988 Analog    5.0 Surround output to Front, Center and Rear speakerssurround51:CARD=Intel,DEV=0    HDA Intel, AD1988 Analog    5.1 Surround output to Front, Center, Rear and Subwoofer speakerssurround71:CARD=Intel,DEV=0    HDA Intel, AD1988 Analog    7.1 Surround output to Front, Center, Side, Rear and Woofer speakersiec958:CARD=Intel,DEV=0    HDA Intel, AD1988 Digital    IEC958 (S/PDIF) Digital Audio Output**** List of PLAYBACK Hardware Devices ****card 0: Intel [HDA Intel], device 0: AD1988 Analog [AD1988 Analog]  Subdevices: 0/1  Subdevice #0: subdevice #0card 0: Intel [HDA Intel], device 1: AD1988 Digital [AD1988 Digital]  Subdevices: 1/1  Subdevice #0: subdevice #0card 0: Intel [HDA Intel], device 2: AD1988 Alt Analog [AD1988 Alt Analog]  Subdevices: 1/1  Subdevice #0: subdevice #0

[/FONT]
[LIST]
[*]Alsamixer F6: Select sound card: nvidia/nvidia-340
[/LIST]
[COLOR=#333333][FONT=UbuntuRegular]   "Error Cannot Can not open mixer device 'nvidia'. No such file or directory"[/FONT][/COLOR]

**LSPCI**
[LIST]
[*]~$ lspci -nn | grep -i audio
[/LIST]
00:1b.0 Audio device [0403]: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller [8086:3a3e]
[LIST]
[*]~$ lspci
[/LIST]
03:00.0 VGA compatible controller: NVIDIA Corporation G84GL [Quadro FX 1700] (rev a1)

**ALSA Information Script**
[LIST]
[*][http://www.alsa-project.org/db/?f=70b4b629b59320afec9c3d7c5f9c4f15d9d7438c](http://www.alsa-project.org/db/?f=70b4b629b59320afec9c3d7c5f9c4f15d9d7438c)
[/LIST]

**Pavucontrol**

[LIST]
[*]No other devices shown?
[/LIST]
[COLOR=#000000][COLOR=#333333][FONT=sans-serif]I am willing to pay to have this fixed, please PM if interested.
Thank you [/FONT][/COLOR][/COLOR]

---

