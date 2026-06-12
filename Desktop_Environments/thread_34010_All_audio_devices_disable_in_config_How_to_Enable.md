---
title: "All audio devices disable in config How to Enable"
date: 2005-05-13
forum: Desktop Environments
---

### Post by dragonopolis on 2005-05-13
Ok my sound card and mic are recognize.  I went to KDE control center and made sure sound was enabled -- it was.  Still no sound?

I went to the info center and click on sound devices and it reports that all sound devices are quote " not enabled in config" 

OK I glanced around in kate at a few conf files to see if I could solve this mystery.
What are the files that info center is reporting "not enabled in config" and what are the settings that I need to change in order to enable it. I still consider
myself a newbie but I catch on pretty quick now with Linux.  

Please help!  My  Synth, MIDI, and Mixer settings are disable in config too.  Can it be edited with Kate?

---

### Post by dacosta123 on 2005-05-13
Spend a whole day on figuring out a similar problem.
Turned out that the module for my particular soundcartd had to be loaded first (which makes sense, after you figured it out).
Using Knoppix 3.8.1 i found out which module i required.

**lsmod** will show you the modules currently loaded
**modprobe xyz** will load the module xyz
Once that is out of the way you should have sound (assuming yours is the same problem  ;-) )

Put xyz in /etc/modules and you should be ok.
I'm not sure whether you should also run update-modules (i'm guessing you should).

Good luck

---

