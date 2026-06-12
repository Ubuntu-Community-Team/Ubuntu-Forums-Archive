---
title: "usb microphone pipeline problem"
date: 2005-08-05
forum: Desktop Environments
---

### Post by art2003 on 2005-08-05
I have a quickcam messanger cam with an integrated microphone.
I have configured the driver and the cam works fine.
Alsamixer lists the microphone Camera (Alsa Mixer)

cat < /dev/dsp2 > /dev/dsp 
works fine (my microphone seems to be configured as /dev/dsp2 )

gnomeMeeting works fine with the mic and the speakers.

Problem comes in gstreamerproperties
The default output sink works fine (ALSA, ESD, OSS)

The default source doesn't.
If I select ALSA (alsasrc) or OSS I get an error message 'Failed to construct test pipeline'
If I select ESD then there is no error but gstreamerproperties crashes.

How can I fix this?

---

