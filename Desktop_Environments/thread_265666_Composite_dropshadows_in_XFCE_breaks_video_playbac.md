---
title: "Composite dropshadows in XFCE breaks video playback."
date: 2006-09-26
forum: Desktop Environments
---

### Post by phibxr on 2006-09-26
Is there any way to play back videos without disabling the hardware acceleration in XFCE? I get black flicker when I try to play videos with VLC or Totem.

Edit: I installed totem-xine with all plugins from Multiverse, and it solved the problem, kind of. The playback drops a few frames on a 2.4ghz CPU, but it is usable enough to watch music vids at least.

---

### Post by ahaslam on 2007-05-14
This is still apparent under Xfce 4.4. 

I have tried adding triple buffering to xorg.conf & enabling sync to vblank within nvidia-settings. Neither showed any improvement. I have tried with numerous players under different distro's to find the same image tearing/frame dropping.

It's been a while since this post was created & there's not much mention of the problem, is there a solution?

---

### Post by ahaslam on 2007-05-18
The problem is not with xfce but xcompmgr as the same damage is observed under gnome.

---

