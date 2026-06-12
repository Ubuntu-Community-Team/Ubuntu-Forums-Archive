---
title: "Sound input in Virtualbox"
date: 2009-06-10
forum: General Help
---

### Post by kg4gyt on 2009-06-10
I can't seem to get a Microphone to work in Virtualbox.  Its working in Ubuntu, and I can hear the input back through the speakers again.  Audio output is working fine.

I'm running Ubuntu 9.04 and Virtualbox 2.2.4.  

Any thoughts?

---

### Post by yaroto98 on 2009-06-10
Can you connect a usb to the VM? You might be able to symbolic-link the camera to the usb interface..... kind of a long shot.

---

### Post by kg4gyt on 2009-06-10
> **yaroto98 said:**
> Can you connect a usb to the VM? You might be able to symbolic-link the camera to the usb interface..... kind of a long shot.

USB Works fine, but I'm a little fuzzy as to where the camera comes in.  There must be a setting somewhere that I'm missing I hope.

---

### Post by tango_ninja on 2011-03-15
For any future viewers of this thread, I had the same problem where audio out worked fine (through internal laptop speakers or headphones) but input via mic was not recognised.

Changing the Virtualbox audio settings from pulse to ASLA fixed this and I can now use my microphone without incident.

---

