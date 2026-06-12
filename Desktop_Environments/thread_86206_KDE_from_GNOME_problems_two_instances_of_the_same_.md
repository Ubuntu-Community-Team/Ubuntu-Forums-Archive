---
title: "KDE from GNOME problems: two instances of the same process"
date: 2005-11-04
forum: Desktop Environments
---

### Post by magnusbb on 2005-11-04
Hello,

I am experiencing a problem related to running some KDE programs from the GNOME environment. For example, when I load JuK it creates two instances of the same process, resulting in more usage of memory and resources. I can afterwords kill one of the two processes, and JuK will continue to function as normal. But why is it creating two instances in the first place?

It is such a waste of resources and annoying.

Additional: When looking at the second process in System Monitor and its open files, I find that they're all related to ALSA. Is ALSA the huge monster behind all this?

Additional II: When it stops playing, the second process quits. It has to be somewhat related to ALSA. It's using GStreamer in stead of aRTs.

---

### Post by Kyral on 2005-11-04
It makes sense that they are all related to ALSA, seeing as ALSA is the sound daemon and controls most sound related things.

But actually I notice it too, 'cept with BMP in XFCE

---

### Post by magnusbb on 2005-11-04
Yes, and it makes sense since GStreamer is not KDE's prefered sound system. But it shouldn't need to duplicate its process... after all, it's all ALSA?

---

### Post by Kyral on 2005-11-04
One process might be the thing itself (like BMP sitting in the corner of my screen) and the other would be the process that it uses to play the sound itself. I dunno, but it kinda makes sense if you think about threads and processes and such

---

