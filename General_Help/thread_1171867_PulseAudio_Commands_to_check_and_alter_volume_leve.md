---
title: "PulseAudio: Commands to check and alter volume level"
date: 2009-05-27
forum: General Help
---

### Post by retrovertigo on 2009-05-27
I've done some googling and found pactl and pacmd, but I still can't figure out a command to get or change the current Master (or any other) volume level.  Does anyone know how to do this?  My goal is to be able to script something to set a specific volume level at login if the volume is below a certain level.

---

### Post by djahma on 2012-05-01
if you do ```
pactl list
``` you would get a list of stuff related to pulseaudio, starting with the loaded modules. After the modules come the sinks. This is where you must spot the device you want to control the volume for. On my pc, I've noted the sink #1 is the one ouputing the sound to my stereo so to control the volume, I would then do ```
pactl set-sink-volume 1 +5%
``` and the volume would increase from, say, 19%, to 24%.
Do 'man pactl' and look for the set-sink-volume option to find about different volume format (e.g. to specify a volume level in décibel).

---

