---
title: "Audio Playback skipping...!?!"
date: 2005-06-16
forum: Desktop Environments
---

### Post by orev on 2005-06-16
Integrated soundcard...

Sound Settings:  16bit, 255ms buffer.

Unable to set priority to "real time" because arts is disabled.

How does one "enable" arts?


Thank you.

Your kindness will be repaid. :)

---

### Post by intangible on 2005-06-17
[QUOTE=orev]Integrated soundcard...

Sound Settings:  16bit, 255ms buffer.

Unable to set priority to "real time" because arts is disabled.

How does one "enable" arts?


Thank you.

Your kindness will be repaid. :)[/QUOTE]
 Do you have arts installed?  If not
**sudo apt-get install arts**

But for most things you should not need it, what application are you playing sounds with?  Try to find an output setting and see if it will let you select ALSA or ESD as those are included with Ubuntu.  I think KUbuntu includes arts instead.

The message you saw may not even be an error message, just an informative one letting you know that it's using a different output other than ARTS.

---

### Post by orev on 2005-06-17
not sure of the default for kubuntu (alsa?), using JuK. Started esd.  Can't adjust volume in volume control now.

tried typing alsa @ terminal > command not found

tried typing sudo apt-get alsa @ terminal > 

"Reading package lists... Done
Building dependency tree... Done
Note, selecting alsa-base instead of alsa
alsa-base is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded."

---

### Post by intangible on 2005-06-22
Sorry, I lost track of this thread, did you get this setup going properly?

---

### Post by orev on 2005-06-22
Yeah.  I got the audio playback going great.  

Now I'm working on my skype headset setup....

Thanks!!

---

