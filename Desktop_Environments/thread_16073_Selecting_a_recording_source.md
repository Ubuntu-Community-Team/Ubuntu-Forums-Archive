---
title: "Selecting a recording source"
date: 2005-02-19
forum: Desktop Environments
---

### Post by sunset_studies on 2005-02-19
Hello all,

I'm having trouble choosing the recording source using the Gnome Volume Control mixer (and any other mixer): there are no 'rec' checkboxes.

I fear this may be because I'm using a USB sound card (hercules muse) and the broken (physically) on board sound is somehow interfering.

The USB card has the usual headphones, microphone, left/right/middle jacks and I got it to "work" (play sound) by removing the driver which the on board sound card needs.

Has anybody else experienced anything similar?

Thanks for any help...

---

### Post by forrestcupp on 2006-06-15
open a terminal window and type      alsamixer

When you are in the mixer hit F4 to switch to your "capture" devices.  This is where you set which one to record from.  In this section, just adjust the volume of the place you want to record from, and turn all the other ones down all the way.  To get back to "playback" devices hit F3.  I haven't been able to find "capture" devices in alsamixergui.  You have to do it with plain alsamixer from the terminal.

---

