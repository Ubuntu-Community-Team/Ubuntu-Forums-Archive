---
title: "Change the volume applet behavior"
date: 2007-08-23
forum: Dell  Ubuntu Support
---

### Post by Molerat on 2007-08-23
Is it possible to change the way the Volume Applet scales the volume?  My problem is that the region of the volume slider that represents reasonable volume is far too narrow,  The bottom half is nearly inaudible while the top quarter is too loud.  I really only have, say, a quarter of the range of the slider at most to adjust the volume level. It is as if the volume is being increased logarithmically where linear stepping might be more appropriate.  Or perhaps the range is too narrow?  I am not sure.

For reference I am using the onboard audio on a Dell XPS 410 with the speark bar on my monitor.  The volume manager is set to HDA Intel (Alsa mixer).

Is there a mixer setting I should look at or something else that might be causing my perceived lack of range in volume?

---

### Post by ridgeland on 2007-08-23
If I single click on the speaker icon in my panel I can adjust the volumne using a small bar.   If I double click on the speaker icon then a window opens.  I can resize this window to be full screen.  Then the slider bar for the volumne is as big as my display.

---

### Post by notwen on 2007-08-23
> **Molerat said:**
> Is it possible to change the way the Volume Applet scales the volume?  My problem is that the region of the volume slider that represents reasonable volume is far too narrow,  The bottom half is nearly inaudible while the top quarter is too loud.  I really only have, say, a quarter of the range of the slider at most to adjust the volume level. It is as if the volume is being increased logarithmically where linear stepping might be more appropriate.  Or perhaps the range is too narrow?

I have similar issues w/ my Dellbuntu Inspiron1420n.  Volume at 50% is barely noticeable(sitting in my lap) and volume at 100% is enough to damage my laptop's speakers, lol.  I have not checked "alsa-mixe"r from the CLI to see what the settings are set to.  Wasn't too concerned about this issue, but if you come across a solution please post back and keep us informed. =]

---

### Post by Molerat on 2007-08-23
I'm making a bit of progress.  When I open alsamixer at the terminal I see that my keyboard hotkeys are altering the FRONT channel in +/-6 units (dB?).  For this channel, 64 and below is nearly inaudible while 94/100 is too loud.  This leaves me with 70, 76, 82, and 88 as my effective volume range.  Now, if I instead control the PCM channel, I have a much wider tolerable volume range and much more fine-grained control.  I have changed Volume Applet to control the PCM channel.

This is where I am stuck.  My keyboard still changes the FRONT channel, and in 6 unit increments.  I do not know how to change this.

---

### Post by Wicca on 2007-08-23
> 
This is where I am stuck.  My keyboard still changes the FRONT channel, and in 6 unit increments.  I do not know how to change this.

Assuming you have Feisty:

Go to System -> Preferences -> Sound, at the bottom choose PCM for your keyboard to control.

---

### Post by Molerat on 2007-08-23
^ Well that was easy enough; thanks.

---

### Post by notwen on 2007-08-25
Maxed out Front in alsamixer and I now control volume through PCM.  Found a nice setting and a very wide audible range from 18% and up.  Thanks all for the info. =]

---

### Post by Wutzl on 2007-10-28
great - going to System - Preferences - Sound and setting the mixer channel to PCM did the trick.

This weird default setting which left only the top 3rd of the volume meter usable has annoyed me long enough - thanks!

---

