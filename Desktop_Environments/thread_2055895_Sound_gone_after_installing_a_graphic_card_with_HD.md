---
title: "Sound gone after installing a graphic card with HDMI"
date: 2012-09-10
forum: Desktop Environments
---

### Post by JanvL on 2012-09-10
Hi,

I have the following mainboard:
M4A88TD-V EVO/USB3
with integrated sound that was working
ALC892 8-Channel High Definition Audio CODEC

After I installed a graphic card my sound is gone, that card is
GeForce GT 220 with HDMI

I am running Ubuntu 12.04 with KDE installed on top.

I have searched the forum and I can even see the bar moving when I say something in the microphone but I do not hear a beep.

Can someone please give me a guide on how to tackle the problem, I know how to give commands in the cli and am not afraid of changing files in /etc but I just cannot get a hold on sound.

Kind regards,
Jan

---

### Post by garyzw on 2012-09-10
You may have to open terminal and start alsamixer and/ or in your sound settings enable [B]S/PDIF audio.
[/B]

---

### Post by JanvL on 2012-09-10
Thaks for the fast reaction!

I had the alsamixer started and saw 00 at S/PDIF and S/PDIF Default I changed it to full volume, no effekt

Card 0  is internal
Card 1 is HDMI (Nvidia)

at settings:
Digital output S/PDIF is on internal audio
Analog Headphone is on internal audio
Analog out is on internal audio
(mind you, translated from german)

the only stange thing I found in the mixer that
/proc/asound/oss/devices does not show a single line

Could that be the problem?

Kind regards,
Jan

---

### Post by youngunix on 2012-09-11
This probably a bit related(maybe not) to your issue, but I had a problem in xbmc where the sound wouldn't work at all, went ahead and installed alsa, rebooted the box and bam! 
in your case, either reinstall alsa or install pulse (log out/log back in and try, if not, reboot).
good luck

---

### Post by JanvL on 2012-09-26
Hi,

I did install alsa new some time ago but I will do that again as soon as I have some time. Who knows . . . 

Kind regards,
Jan

---

### Post by JanvL on 2012-12-18
Well,

I installed ALSA new but no effect.

Does anyone know a step by step howto through which one can checkout the sound-seettings?

I have found all kind of good advice but with very different solutions  and no one seem to tackle the problem I have.

Kind regards,
Jan

---

### Post by RitzBitzN on 2012-12-19
I know how to fix this ... I think I had a similar problem. Run kMix from the application launcher (you are using KDE, so it should be built in), and then click 'Settings' and then 'Select Master Channel' and then choose 'Built-In ...' to choose your motherboard audio. Hope this helps!

---

### Post by dannyboy79 on 2012-12-19
are you wanting the sound to go thru your HDMI port or are you only using your nvidia card for it's graphics?

I recently installed a 8400 GS and had the same issue. it has to do with setting the correct sound card as the default one. follow "Ad" here: [https://help.ubuntu.com/community/SoundTroubleshootingGuide](https://help.ubuntu.com/community/SoundTroubleshootingGuide)

and make sure within pavucontrol everything is set correctly and alsamixer has volumes unmuted and turned up

---

### Post by JanvL on 2012-12-19
Hi,

That is exactly what I want.
"or are you only using your nvidia card for it's graphics"

Sorry RitzBitzn, that did not do it so I will have to try
Dannyboy79's solution.

Thank you for responding,
kind regards,
Jan

---

### Post by JanvL on 2012-12-19
Hi

I see in the alsamixer S/PDIF and S/PDIF default both at 00,
but I do not know how to raise the levels, the pointerkeys do not work there.

What could be the cause?


Here is a listing of the shell-commands:

jan@Linux01:~$ aplay -l
**** Liste der Hardware-Geräte (PLAYBACK) ****
Karte 0: SB [HDA ATI SB], Gerät 0: ALC892 Analog [ALC892 Analog]
  Sub-Geräte: 1/1
  Sub-Gerät #0: subdevice #0
Karte 0: SB [HDA ATI SB], Gerät 1: ALC892 Digital [ALC892 Digital]
  Sub-Geräte: 1/1
  Sub-Gerät #0: subdevice #0
Karte 1: NVidia [HDA NVidia], Gerät 3: HDMI 0 [HDMI 0]
  Sub-Geräte: 1/1
  Sub-Gerät #0: subdevice #0
Karte 1: NVidia [HDA NVidia], Gerät 7: HDMI 0 [HDMI 0]
  Sub-Geräte: 1/1
  Sub-Gerät #0: subdevice #0
Karte 1: NVidia [HDA NVidia], Gerät 8: HDMI 0 [HDMI 0]
  Sub-Geräte: 1/1
  Sub-Gerät #0: subdevice #0
Karte 1: NVidia [HDA NVidia], Gerät 9: HDMI 0 [HDMI 0]
  Sub-Geräte: 1/1
  Sub-Gerät #0: subdevice #0

jan@Linux01:~$ lspci -nn | grep '\[04[80][13]\]'
00:14.2 Audio device [0403]: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA) [1002:4383] (rev 40)
01:00.1 Audio device [0403]: NVIDIA Corporation High Definition Audio Controller [10de:0be2] (rev a1)

So both are "seen".

just made a /etc/sound/asound.conf

pcm.!default {
type plug slave.pcm {
type hw card 0 device 1
}
}

rebooted, but after a sharp tic at boottime, no sound.



Kind regards,
Jan

---

### Post by dannyboy79 on 2012-12-19
you have a your speakers connected to the green plug on your computer? if so, you need to change your device to 0, that's the analog audio. Here's some picture of my setup and aplay -l and /etc/asound.conf file and my sound works just fine with an 8400 GS Nvidia HDMI card.
this is within pavucontrol
[IMG]https://lh5.googleusercontent.com/-wW5_T22KgTk/UNJUtnlE5KI/AAAAAAAAAxY/JyamEftzRvo/s1066/pulseaudio_config.png[/IMG]

[IMG]https://lh4.googleusercontent.com/-OvNUmieCWWE/UNJUvRwkZ8I/AAAAAAAAAxg/yNPrXk7-mb0/s1049/pulse_output.png[/IMG]

aplay -l
```

**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 7: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 8: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 9: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: VT82xx [HDA VIA VT82xx], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: VT82xx [HDA VIA VT82xx], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

/etc/asound.conf
```
pcm.!default {
      type plug slave.pcm {
            type hw card 2 device 0
      }
}

```

---

### Post by JanvL on 2012-12-21
Hi,

some progress is there.

I have put the right device in and checked I am plugged in to the green plug.
With pavucontrol I seen the analog port and when I click on the symbol to mute, I here a click in the speakers and see the bar jump.

I just do not get sound . . . 

Before I did put in the graphic card, I had the "Digital Stereo AC958 Output + Analog Stereo Input". I would like to use the mic as well (skype).
If I choose that I do not hear a click when I click mute.

I must be overlooking something.

Kind regards,
Jan

---

### Post by dannyboy79 on 2012-12-21
ensure all alsamixer settings have 00 and not MM, also, under the configuration tab put it to Analog Stereo Duplex, you'll be able to use a microphone with skype. those pictures are how my system is setup and i can use my mic.

---

