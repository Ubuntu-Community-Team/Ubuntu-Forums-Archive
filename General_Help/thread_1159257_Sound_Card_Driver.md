---
title: "Sound Card Driver"
date: 2009-05-14
forum: General Help
---

### Post by chriswinsatlife on 2009-05-14
I was having problems with GTKRecordMyDesktop, and found an article online saying that installing alsa-driver-1.0.14 enabled it to work. I installed this via terminal and nothing happened, but ultimately figured out how to fix the problem in GTKRMD (record from plughw:0,0). 

Anyway, on reboot no sound works because obviously I changed the sound driver, and now I can't fix it. I did a "make uninstall" in the alsa-driver-1.0.14 directory, but no dice. Clicking on the tray volume icon yield "No volume control GStreamer plugins and/or devices found."

How do I fix this? Do I roll back to the previous sound card driver? (and if so, how?)

Thanks for the help.

---

