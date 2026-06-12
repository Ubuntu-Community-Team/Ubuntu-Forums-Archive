---
title: "System sound volume"
date: 2006-05-16
forum: Desktop Environments
---

### Post by i++ on 2006-05-16
I have a problem with my sound, im using ALSA, and i have a volume contol on a panel, and on my keyboard, and when i change it it doesnt change the volume of Rhythmbox. I have to open Rhythmbox and change the volume in there. Any idea how I can make  the system volume (or thats what it seems) be the same as the Rhythmbox volume? 

thanks in adnvance

---

### Post by Sutekh on 2006-05-17
The volume control in the panel can only control the one output channel at a time.  Make sure that the volume control on the panel is controlling the correct channel, the same one that RB is using.  

You should be able to right-click on the volume control and select Preferences.  From there you should be able to choose the output channel from a drop down menu.

If you find the output channel that your sound is using, then changing that volume will change the volume coming from RB and any other sound applications, effectively you are controlling the 'system' volume.  (This is not the same as changing RB's internal volume)

---

### Post by Godzig on 2006-09-07
I have the same problem though am making some progress.  I got the panel volume to change the actual speaker output by having it focus on the PCM output instead of the master volume.

But now I can't figure out how to get the keyboard shortcuts to map to PCM as well; the volume up/down keys are configured with keyboard shortcuts but they seem willing to only effect the master volume. Is there a way to link the keyboard shortcut keys to whatever the volume applet in the panel is focused on? (the matching icons made me think they were linked, but perhaps no).

---

