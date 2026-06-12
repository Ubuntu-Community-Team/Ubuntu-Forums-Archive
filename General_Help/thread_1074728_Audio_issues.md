---
title: "Audio issues"
date: 2009-02-19
forum: General Help
---

### Post by Patricrawley on 2009-02-19
I use ALSA for all my sound settings and it works fine, no issues at all. However, every single time I boot up I have to kill the pulseaudio process. How do I stop pulseaudio from starting at all?

---

### Post by anlag on 2009-02-19
See the initial post of this topic for instructions on how to uninstall pulse:

[http://ubuntuforums.org/showthread.php?t=973637](http://ubuntuforums.org/showthread.php?t=973637)

I suppose if you for some reason don't want to uninstall it but just prevent it from starting, you could unclick it under Preferences -> Sessions -> Startup Programs. I haven't tried that though - simply threw it out as it was causing increasing delays in outgoing sound in Skype.

---

### Post by mikewhatever on 2009-02-19
First there is a startup process to remove in System/Preferences/Sessions. On the other hand, since you don't use pulseaudio, consider removing it from the system.

---

