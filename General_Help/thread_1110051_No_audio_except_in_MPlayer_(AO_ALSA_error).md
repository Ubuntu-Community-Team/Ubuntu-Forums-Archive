---
title: "No audio except in MPlayer (AO_ALSA error)"
date: 2009-03-29
forum: General Help
---

### Post by nunyez on 2009-03-29
Im running ibex. MPlayer is the only app that my audio will work with. Everything else locks up. When I play something in MPlayer it prompts a dialog with: "[AO_ALSA] Unable to set hw-parameters: Input/output error". 

My PulseAudio shows no Output Devices.

---

### Post by ethoxyethaan on 2009-03-29
type:

gstreamer-properties

and try messing arround with that.

also post the output of:

cat ~/.mplayer/gui.conf | grep ao_driver

---

### Post by nunyez on 2009-03-29
ao_driver = "pulse,alsa,"

gstreamer properties results:
"Autodetect: Fail to connect stream: Invalid argument"
"ALSA - Advanced Linux Sound Architecture: Could not get/set resources from/on resource."
OSS Open Sound System = **SUCCESS!**
"PulseAudio Sound Server: Failed to connect stream: Invalid argument"

I set the default output in gstreamer-properties to OSS. Rhythmbox and others still lock up. Now what?

---

### Post by nunyez on 2009-03-29
help greatly appreciated

---

### Post by ethoxyethaan on 2009-03-29
if mplayer works on Alsa then gstreamer should work with alsa aswell instead of oss. 
try setting the options on alsa on everything else.

Try restarting your session as well.

---

