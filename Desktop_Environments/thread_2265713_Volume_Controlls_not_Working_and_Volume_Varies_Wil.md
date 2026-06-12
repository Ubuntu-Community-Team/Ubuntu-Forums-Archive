---
title: "Volume Controlls not Working and Volume Varies Wildly with Output Method"
date: 2015-02-17
forum: Desktop Environments
---

### Post by csiebester on 2015-02-17
I'm running Lubuntu 14.04 on a Dell Inspiron 1100

If I set the volmue with my headphones unplugged and then plug in my headphones they are about loud enough to make my ears bleed and if I set for headphones and unplug, the speakers are almost silent.  Also the Ubuntu volume control doesn't work on the headphones.  Using headphones the controlls for what I'm listening to (usually internet music or video) work but in a non linear way such that almost all of the volume adjustment happens in the bottom 10% of the slider.  It's almost impossible to get the correct volume with headphones as a result.  The Ubuntu volume controll does work with the built in speakers.

---

### Post by ajgreeny on 2015-02-17
I can't remember if Lubuntu has pulseaudio installed by default but if not, install it using synaptic.

You will then be able to set the volume of speakers and headphones separately using Sound-settings from the volume icon in the panel.

---

### Post by BazBear on 2015-02-17
> **ajgreeny said:**
> I can't remember if Lubuntu has pulseaudio installed by default but if not, install it using synaptic.

You will then be able to set the volume of speakers and headphones separately using Sound-settings from the volume icon in the panel.
Lubuntu doesn't include it, and I can't recall if installing the pulse audio main package pulls in the control panel for it too, so csiebester might need the pavucontrol package as well.

---

