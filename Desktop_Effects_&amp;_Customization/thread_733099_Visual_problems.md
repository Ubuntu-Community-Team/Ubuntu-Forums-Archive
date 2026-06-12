---
title: "Visual problems"
date: 2008-03-23
forum: Desktop Effects &amp; Customization
---

### Post by danielland on 2008-03-23
Since getting my visual effects running by downloading the linux drivers for my graphics card (RV350 AS [Radeon 9550]) i now have a flickering problem with my visualisations in music players and also it will only play videos avi etc in full screen..

Any ideas

---

### Post by Ub1476 on 2008-03-23
It's because the ATI driver doesn't support video playback while running Compiz. Hopefully this will be added soon. In VLC though, you can set it to use X11 in Settings>Video>Output Modules, so it wont flicker.

---

### Post by danielland on 2008-03-23
Im not being clever here i do not think but what did you mean 

settings in vlc yes? What is x11 and module output modules?

---

### Post by Ub1476 on 2008-03-23
VLC>Settings>Preferences>Video>Output modules>Advanced options>X11 video output.

---

### Post by danielland on 2008-03-23
i cant see this x11 option in advanced options

---

### Post by Ub1476 on 2008-03-23
Output modules>Video output modules>Change from default to X11 video output.

---

### Post by knowledge_is_power on 2008-03-25
you could also try disabling the Xvideo extension.  this might cause a slow in videos, but it might (??) get rid of flicker.  run gstreamer-properties and goto video and select the X version with no Xv, then click test.  if you get a good picture, give it a shot.
:guitar:

---

