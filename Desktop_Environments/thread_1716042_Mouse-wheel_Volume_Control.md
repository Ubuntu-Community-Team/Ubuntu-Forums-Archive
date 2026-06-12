---
title: "Mouse-wheel Volume Control"
date: 2011-03-27
forum: Desktop Environments
---

### Post by stevo1977 on 2011-03-27
This is super trivial, but since upgrading to meerkat (after manually adding gnome-volume-control-applet back to the taskbar) my mouse-wheel adjusts the volume in increments of 5 instead of whatever smaller number it used to be (1? 3?).  Is there any way to change this?  This was a tough one to google, and nothing I found seemed to address this (very minor) issue.  Thanks for your help.

---

### Post by redfireplace on 2011-10-20
I've wanted to know how to do this for a long time. Is the amount the volume changes by hard coded, or is there a config file I can edit?

---

### Post by Frogs Hair on 2011-10-20
Check the configuration editor ; although , I've  never noticed such a setting I haven't looked for one .

---

### Post by stevo1977 on 2011-10-20
I never did figure out how to adjust this, but I noticed that it is hardware specific.  For instance, my mouse's scroll-wheel adjusts the volume by 5 but the volume knob on my keyboard adjusts the volume by 6.  This leads me to believe that it depends on how scaling inputs from the hardware and has nothing to do with the sound manager.  Just a thought.

Cheers,
stevo

---

### Post by redfireplace on 2011-10-21
I opened configuration editor and went to apps/gnome_settings_daemon/volume_step. I think the default value was 5. I can change it, but it has no effect on anything that I can see. Using the scroll wheel over the volume control is always the same regardless of the value of volume_step. Same thing with all the other volume sliders.

This is in Natty Narwhal.

---

