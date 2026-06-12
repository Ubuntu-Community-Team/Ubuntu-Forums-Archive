---
title: "Ubuntu 16.04 no sound in the speakers or headphones"
date: 2017-09-05
forum: Desktop Environments
---

### Post by dhira on 2017-09-05
Hi, I have HP 655 notebook and after installing 16.04 there is no sound either through the speakers, nor the headphones nor does it record through built in mic. Me and my friend tried different things. It worked fine on 14.04.

   Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Wrestler HDMI Audio
 
 
  List of Hardware Devices (PLAYBACK) ****
 Karte 0: Generic [HD-Audio Generic], Device 3: Generic Digital [Generic Digital]
   Sub-Device: 0/1
   Sub- Device #0: subdevice #0
 Karte 1: Generic_1 [HD-Audio Generic], Device 0: ALC269VC Analog [ALC269VC Analog]
   Sub-Device: 1/1
   Sub- Device #0: subdevice #0
 Karte 1: Generic_1 [HD-Audio Generic], Device 1: ALC269VC Digital [ALC269VC Digital]
   Sub-Device: 1/1
   Sub- Device #0: subdevice #0

Any help appreciated. Thank you in advance.

---

### Post by dhira on 2017-09-05
Here additional information:

aplay -L
default
    Playback/recording through the PulseAudio sound server
null
    Discard all samples (playback) or generate zero samples (capture)
pulse
    PulseAudio Sound Server
hdmi:CARD=Generic,DEV=0
    HD-Audio Generic, Generic Digital
    HDMI Audio Output
dmix:CARD=Generic,DEV=3
    HD-Audio Generic, Generic Digital
    Direct sample mixing device
dsnoop:CARD=Generic,DEV=3
    HD-Audio Generic, Generic Digital
    Direct sample snooping device
hw:CARD=Generic,DEV=3
    HD-Audio Generic, Generic Digital
    Direct hardware device without any conversions
plughw:CARD=Generic,DEV=3
    HD-Audio Generic, Generic Digital
    Hardware device with all software conversions
sysdefault:CARD=Generic_1
    HD-Audio Generic, ALC269VC Analog
    Default Audio Device
front:CARD=Generic_1,DEV=0
    HD-Audio Generic, ALC269VC Analog
    Front speakers
surround21:CARD=Generic_1,DEV=0
    HD-Audio Generic, ALC269VC Analog
    2.1 Surround output to Front and Subwoofer speakers
surround40:CARD=Generic_1,DEV=0
    HD-Audio Generic, ALC269VC Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Generic_1,DEV=0
    HD-Audio Generic, ALC269VC Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Generic_1,DEV=0
    HD-Audio Generic, ALC269VC Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Generic_1,DEV=0
    HD-Audio Generic, ALC269VC Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Generic_1,DEV=0
    HD-Audio Generic, ALC269VC Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Generic_1,DEV=0
    HD-Audio Generic, ALC269VC Digital
    IEC958 (S/PDIF) Digital Audio Output
dmix:CARD=Generic_1,DEV=0
    HD-Audio Generic, ALC269VC Analog
    Direct sample mixing device
dmix:CARD=Generic_1,DEV=1
    HD-Audio Generic, ALC269VC Digital
    Direct sample mixing device
dsnoop:CARD=Generic_1,DEV=0
    HD-Audio Generic, ALC269VC Analog
    Direct sample snooping device
dsnoop:CARD=Generic_1,DEV=1
    HD-Audio Generic, ALC269VC Digital
    Direct sample snooping device
hw:CARD=Generic_1,DEV=0
    HD-Audio Generic, ALC269VC Analog
    Direct hardware device without any conversions
hw:CARD=Generic_1,DEV=1
    HD-Audio Generic, ALC269VC Digital
    Direct hardware device without any conversions
plughw:CARD=Generic_1,DEV=0
    HD-Audio Generic, ALC269VC Analog
    Hardware device with all software conversions
plughw:CARD=Generic_1,DEV=1
    HD-Audio Generic, ALC269VC Digital
    Hardware device with all software conversions

---

### Post by Autodave on 2017-09-06
Did you do a new install of 16.04 or did you upgrade from 14.04 to 16.04?

---

### Post by dhira on 2017-09-06
I did a new install of 16.04 LTS.

---

### Post by lammert-nijhof on 2017-09-06
Look in PulseAudio Volume Control (pavucontrol) in the Configuration tab. You might have to install that program, because it is not installed by default. You seem to have two audio controllers, probably one is using a HDMI video plug to transport the audio belonging to the video and the other is the controller connected to the speakers and/or headphone. Switch that HDMI audio controller "off" in the configuration tab. If you are using e.g. a TV to play videos and you can't switch off the HDMI controller, you can select the right audio controller for each program using the buttons right to the program name in the playback and recording tabs. The system will remember you selection forever.

---

### Post by dhira on 2017-09-07
Dear Lammert-nijhof, I did exactly as you wrote and it worked fine  with PulseAudio Volume Control! I managed to switch the HDMI audio  controller off. Thank you so much!

---

### Post by john164 on 2018-02-02
bang on for me too, thanks

---

### Post by static7 on 2018-07-13
Just wanted to say thank you. pavucontrol worked fantastically.

---

