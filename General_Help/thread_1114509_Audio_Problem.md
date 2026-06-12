---
title: "Audio Problem"
date: 2009-04-02
forum: General Help
---

### Post by THdragon on 2009-04-02
I'm having a major problem, Ubuntu is not picking and audio speakers or headphones. 

The cotrol panel is off and when i try to open it I get this:

No volume control GStreamer plugins and/or devices found.




Everything is plugged into the right slots, This happened suddenly after i restarted my comp one time, while I was trying to fix my mic.

Does anyone know what to do and/or help me?

---

### Post by JC Cheloven on 2009-04-02
Is your device selected, and your output unmutted? 
You can check it out clicking twice in the speaker icon at the upper panel, or typing "sudo alsamixer" at terminal.

Otherwise, please have a look on this [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by connorh123 on 2009-04-02
This has gotta be my 5th time seeing an audio problem. No matter, I like helping out.
Type this into terminal:
> sudo apt-get install kmix
After it installs, it should start up, if not type kmix.
Then go into settings and turn up your audio.

---

