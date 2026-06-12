---
title: "&quot;Dracula: the vampire strikes back&quot; produces no sound"
date: 2014-12-15
forum: Gaming &amp; Leisure
---

### Post by i12 on 2014-12-15
I've installed "Dracula: the vampire strikes back" game but it produces no sound. Sound file is definitely downloaded. Alsa applications souns very quetly. What to do?

---

### Post by Elfy on 2014-12-15
*Thread moved to **Gaming & Leisure**.*

---

### Post by ajgreeny on 2014-12-15
> **i12 said:**
> I've installed "Dracula: the vampire strikes back" game but it produces no sound. Sound file is definitely downloaded. Alsa applications souns very quetly. What to do?
Check the volume levels in both **alsamixer** in terminal and also **pulseaudio-volume-control** which you can get to by clicking the volume icon in the panel ->Sound Settings.

---

### Post by i12 on 2014-12-16
Ok. I had to chek output device in control panel. Strange, jack apps worked without this.I tried another applications (zynaddsubfx, bristol) - they sound quetly (low sound level).

> **ajgreeny said:**
> Check the volume levels in both **alsamixer** in terminal and also **pulseaudio-volume-control** which you can get to by clicking the volume icon in the panel ->Sound Settings.
I cant find and cant install **pulseaudio-volume-control. **My system is  14.10 with Gnome.

---

### Post by sffvba[e0rt on 2014-12-16
> **i12 said:**
> Ok. I had to chek output device in control panel. Strange, jack apps worked without this.I tried another applications (zynaddsubfx, bristol) - they sound quetly (low sound level).


I cant find and cant install **pulseaudio-volume-control. **My system is  14.10 with Gnome.

The package you are looking for is called pavucontrol. -*** sudo apt-get install pavucontrol*** (in terminal)

---

### Post by i12 on 2014-12-19
***pavucontrol ****cant help*

---

