---
title: "ubuntu 16.04 no sound via the laptop speakers"
date: 2017-08-27
forum: Desktop Environments
---

### Post by zozonmr on 2017-08-27
Hi all,

I have recently installed ubuntu 16.04 on an asus laptop next to windows 10. everything seems to work quite well apart from the sound via the speakers of the laptop. The audio jack works and there sound if a device is plugged in. The lspci command gives this audio device:

Audio device: Intel Corporation Device a171 (rev 31)

the result of the aplay -l command is:

**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC233 Analog [ALC233 Analog]
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

I have made some google searches and found that this can happen however the soltuions presented there did not solve my problem! I have reinstalled the alsa-utils packages and also pulseaudio. Also tried Alsamixer and pavucontrol. 
Somehow nothing seems to give me sound via the built in speakers. 

Anybody any idea what could go on here? 

Thanks!

---

### Post by ajgreeny on 2017-08-27
Does pavucontrol show both the external speakers and the internal speakers in the output devices and if it does (it certainly should do so) what volumes are shown for each of them?

---

### Post by zozonmr on 2017-08-28
Hi,

When I plug in my headphones then [COLOR=#000000] pavucontrol shows both (speakers unavailable and headphone plugged in) in the Output Devices section and the the sound is set to max in both however if I choose the speakers then the headphone goes silence but the speakers do not go on. 
In the configuration set-up of [/COLOR][COLOR=#000000] pavucontrol there are multiple options and currently it is set to Analogue stereo duplex. 
[/COLOR][COLOR=#000000]When I unplug the headphones only the speakers are available but no sound is coming out of the speakers.  There is one weird thing in [/COLOR][COLOR=#000000] pavucontrol. There is a bar signalling whether there is sound or not when it is on speaker it still shows that there is sound!?!?[/COLOR]

---

### Post by zozonmr on 2017-09-03
Hi,

To whom it may concern,

So Magical from one day to another the sound started playing in the laptop speakers. The  pavucontrol's has to be set to analogue stereo duplex and it has to be done after ubuntu has booted in. It will automatically jump to the HDMI option which obviously is not connected. So the task to find how to set the analogue stereo duplex as default. The good news is that the sound plys very well over any of the connections. It is just a bit tiresome to switch manually to the laptop speakers! 

Thanks!

---

### Post by lammert-nijhof on 2017-09-03
I always disable the HDMI option in pavucontrol configuration tab, because I never use it. The alternative is that in the playback tab for your audio producing programs you choose the right device for that program, so for Rhythmbox it would be your 'Built-in Audio Analog Stereo'. The system will remember you choice forever.

---

