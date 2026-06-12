---
title: "Sound no longer working?"
date: 2011-06-10
forum: Desktop Environments
---

### Post by neu5eeCh on 2011-06-10
I've been using Xubuntu 11.04 relatively successfully for several weeks now. I new problem has arisen. The sound suddenly stopped working. I think it has something to do with the built-in session manager and, possibly, the fact that I have installed gnome-based multimedia apps? - but I don't know. First question: If the session manager is somehow responsible, how do I restart sound?

Secondly, the session manager seems like it's been causing nothing but trouble? How does one uninstall this feature in Xubuntu? - is it recommended?

**Edit:** I *may* have solve this myself. I started "mixer" using Gnome-do. Under playback, I was asked which controls to use. There were two options: HDA Intel (Alsa Mixer); & Inernal Audio Analog Stereo (PulseAudio Mixer). I picked the second and checked "Master" as the controls. I have no idea why or how "master" had been unchecked (except that I've installed some Gnome components). I also installed gconf shortly before having these troubles (in order to activate clutterflow in Nautilus Elementary).

---

