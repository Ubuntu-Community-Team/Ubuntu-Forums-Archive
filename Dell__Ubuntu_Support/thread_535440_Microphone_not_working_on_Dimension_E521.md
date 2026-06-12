---
title: "Microphone not working on Dimension E521"
date: 2007-08-26
forum: Dell  Ubuntu Support
---

### Post by baupres on 2007-08-26
I have installed Ubuntu 6.06 on a Dell E521. The problem I have is the microphone is not working.

If I start the Sound Recorder program and I go to FILE-OPEN VOLUME CONTROL  I can only find two tabs: PLAY and OPTIONS but not the CAPTURE tab. So I can not select microphone levels or active it in any way.It seems like it is not supported by current alsa drivers. The microphone is working in Windows Vista.

My hardware is: 
Onboard audio card chip SigmaTel STAC9227
Video Card: NVIDIA Geforce 6150LE
Processor: AMD 64x2 4200

Any idea?

---

### Post by linuxwizard on 2007-08-26
[https://help.ubuntu.com/community/AudioCapture](https://help.ubuntu.com/community/AudioCapture)

[http://ubuntuforums.org/showthread.php?t=385739&highlight=HOWTO+microphone](http://ubuntuforums.org/showthread.php?t=385739&highlight=HOWTO+microphone)

---

### Post by baupres on 2007-08-26
I have already tried the recomendations contained in the links and I have not obtained a solution for the microphone.

I include a picture of my volume control. As you can see there is no capture tab. I have explored all the options and I have obtained no way to show the capture tab, Only Playback and Options. (sorry, my Ubuntu is in Spanish, but I am sure you will figure it up).

[IMG]http://img.godlike.cl/images/Volume.png[/IMG]

---

### Post by baupres on 2007-08-27
It seems like a known bug #42600 in linux-source that has been discussed in 

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/42600](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/42600)

Other info: 

~$ arecord -l
**** Lista de CAPTURE Dispositivos Hardware ****
tarjeta 0: NVidia [HDA NVidia], dispositivo 0: STAC92xx Analog [STAC92xx Analog]  Subdispositivos: 2/2
  Subdispositivo #0: subdevice #0
  Subdispositivo #1: subdevice #1

~$ amixer
Simple mixer control 'PCM',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%]
  Front Right: Playback 255 [100%]
Simple mixer control 'Front',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 127
  Mono:
  Front Left: Playback 102 [80%] [on]
  Front Right: Playback 102 [80%] [on]
Simple mixer control 'Surround',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 127
  Mono:
  Front Left: Playback 127 [100%] [off]
  Front Right: Playback 127 [100%] [off]
Simple mixer control 'Center',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 127
  Mono: Playback 127 [100%] [off]
Simple mixer control 'LFE',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined
  Playback channels: Mono
  Limits: Playback 0 - 127
  Mono: Playback 127 [100%] [off]
Simple mixer control 'Side',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 127
  Mono:
  Front Left: Playback 127 [100%] [on]
  Front Right: Playback 127 [100%] [on]
Simple mixer control 'ADCMux',0
  Capabilities: cswitch
  Capture channels: Front Left - Front Right
  Front Left: Capture [off]
  Front Right: Capture [off]
Simple mixer control 'InMux',0
  Capabilities: cvolume
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 4
  Front Left: Capture 4 [100%]
  Front Right: Capture 4 [100%]
Simple mixer control 'InVol',0
  Capabilities: cvolume
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 14
  Front Left: Capture 14 [100%]
  Front Right: Capture 14 [100%]
Simple mixer control 'Input Source',0
  Capabilities: enum
  Items: 'Mic' 'Front Mic' 'Line'
  Item0: 'Mic'

Let me know if there's anything else I can do to help diagnose this.

Any suggestion?

---

### Post by brennydoogles on 2007-08-29
I am having the same problem, and i would love to have a solution as well (as this is one of the last things keeping me on a dual boot. Thanks for the help!!

---

### Post by baupres on 2007-09-01
> **brennydoogles said:**
> I am having the same problem, and i would love to have a solution as well (as this is one of the last things keeping me on a dual boot. Thanks for the help!!

Are you having the same problem with Ubuntu 7.04 too? Do you think it is a general linux bug or only ubuntu problem? Have you ever tried SuSe or Mandriva with Dimension E521?

---

### Post by brennydoogles on 2007-09-01
> **baupres said:**
> Are you having the same problem with Ubuntu 7.04 too? Do you think it is a general linux bug or only ubuntu problem? Have you ever tried SuSe or Mandriva with Dimension E521?

Ubuntu is the only distro I have ever used. Maybe I will try a live cd to see if I can duplicate the problem with another distro. The microphone I have works on my Windows boot, so I know it is not the mic.

---

### Post by baupres on 2007-09-13
I have tried with a PCLinuxOS live cd and .... I have had any problem at all! It has automatically detected all hardware: the nvidia graphic card, the sound card, printers...I have even tried to install skype (remember: on the live cd, not on the hard disk) through synaptic.... and voila... the microphone works flawlessly...

Incredible distro PCLinuxOS... I am still surprised. Try it and tell me back about it.

... and its very fast too.

---

### Post by brennydoogles on 2007-10-18
After my upgrade to Gutsy the microphone is working perfectly!! Very very happy!

---

### Post by baupres on 2007-12-11
> **brennydoogles said:**
> After my upgrade to Gutsy the microphone is working perfectly!! Very very happy!

Can you please post your configuration? My microphone keeps not working at all. :confused:

---

### Post by baupres on 2007-12-14
> **baupres said:**
> Can you please post your configuration? My microphone keeps not working at all. :confused:

Resolved it by adding

Code:

```
 options snd-hda-intel model=3stack

```


to /etc/modprobe.d/alsa-base
rebooting then opening up the volume control and pushing capture up to 100% and changing the Input Source to Front Mic.:)

---

### Post by SaberCat on 2008-01-06
Yes I had the same problem with Sound Recorder (aka, gnome-sound-recorder) -- it didn't  work for me running 7.04 on a Dell Dimension E521. Try using arecord, the ALSA program for recording:

arecord -r 44100 -c 2 -f S16_LE test.wav

That worked for me. Also, the recorder in Audacity worked...

---

