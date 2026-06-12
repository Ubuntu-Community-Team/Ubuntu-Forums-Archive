---
title: "help me, desktop and touchpad dx locked =("
date: 2009-01-27
forum: Desktop Environments
---

### Post by grifisx on 2009-01-27
After i have installed, from sources, latestes gstreamer and other package, my desktop was locked.
When start a nautilus windows open and closed fast 4-5 times then, no icon, dx touchpad button is locked (only on-desktop), rhythmbox don't play music because say that not find folders, no more audio preview.
But the audio work fine.
I have removed the new packages and reinstalled the old, but nothing... if a add a new user some trouble.
Sorry my english =I
help...

---

### Post by adamlau on 2009-01-27
What other packages did you install? You may have to compile Rhythmbox against the new libraries. How did you remove the new packages? How did you reinstall the old? Did you purge the configuration files in between (recommended as upstream syntax changes may be partially at fault)?

---

### Post by grifisx on 2009-01-27
> **adamlau said:**
> What other packages did you install? You may have to compile Rhythmbox against the new libraries. How did you remove the new packages? How did you reinstall the old? Did you purge the configuration files in between (recommended as upstream syntax changes may be partially at fault)?
gst-plugins-base-0.10.21 
nice-0.0.4
pygtk-2.12.1
gst-python-0.10.14
gstreamer-0.10.22
farsight2-0.0.7
I have installed source with checkinstall
I removed -purge the news with synaptic, and reinstall the old with synaptic.
o.o ..and now ..there is a solution?

Update:
I have purged rhytmobx and reinstall, now work, also work the music preview, but desktop is locked and also dx button on it.

---

