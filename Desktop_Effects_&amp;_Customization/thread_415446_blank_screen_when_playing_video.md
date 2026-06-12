---
title: "blank screen when playing video"
date: 2007-04-20
forum: Desktop Effects &amp; Customization
---

### Post by iffans on 2007-04-20
I've installed Feisty this morning and Desktop Effects work out-of-the-box. However, when I play video, i can't see anything but hear the sound. If I minimize-maximize the video it seems its properly running "behind" the screen. This only happens with effects enabled. I have an ATI card, tried to install the restricted drivers, but couldn't start effects as there was a problem about "composite option" availability so I went back to the open drivers. Any ideas?

---

### Post by deromka on 2007-04-21
Have the same problem on Thinkpad T42p with Mobility FireGL T2. The screen is black only when plaing video with Desktop Effects on.

this can be solved by openning gstreamer-properties and changing in video tab
 Default Output plugin to X window System (No XV)

---

### Post by iffans on 2007-04-21
already done it and works great :)

---

