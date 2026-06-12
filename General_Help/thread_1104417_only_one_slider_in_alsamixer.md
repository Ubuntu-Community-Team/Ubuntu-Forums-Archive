---
title: "only one slider in alsamixer"
date: 2009-03-23
forum: General Help
---

### Post by gamewolf on 2009-03-23
I have ALSA installed. The sound is coming out kinda quiet (not a big deal), but I cannot get the mic working. In alsamixer, there is only one slider and its Master. There are usually 6 on my other installs for ubuntu. I have gone to volume control in Gnome and am still unable to get the mic to work. I have tried recording with Audacity and Gnome Sound Recorder.

What the heck is goin on?

BTW, I followed the guide to installing OSS (this was when my sound wouldn't work at all). It screwed things up even more. I worked my way backwards through the tutorial to get Alsa installed again and I now have sound (although quiet). This could be something to do with my problems.

---

### Post by gamewolf on 2009-03-23
bump

---

### Post by gamewolf on 2009-03-23
bump again

---

### Post by fooman on 2009-03-23
try the gnome-alsamixer.  it is in the repos,  so you can install it through add/remove or synaptic.

or just run this in a terminal:

```
sudo aptget install gnome-alsamixer
```after it installs,  find it in applications > sound & video....open it and see if there are more sliders to play around with.

hope that helps.

---

### Post by gamewolf on 2009-03-24
That did the trick. Thanks for the help

---

