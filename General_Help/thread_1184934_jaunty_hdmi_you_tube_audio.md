---
title: "jaunty hdmi you tube audio"
date: 2009-06-11
forum: General Help
---

### Post by koscica on 2009-06-11
Hi I'm a new Ubuntu user and I just installed Jaunty on my brand new ASUS P4-P5N9300 with an integrated geforce 9300 card. I have the latest Nvidia and Alsa drivers installed and I managed to get audio to work over HDMI on everthing except on you tube videos.
 
Any help would be appreciated.

---

### Post by koscica on 2009-06-15
If anyone is interested the solution was to create a file ~/.asoundrc:
 
 
pcm.!default {
type asym
playback.pcm {
type plug
slave.pcm "hw:0,3"
}
}

---

### Post by silvertuna on 2009-08-10
How did you get HDMI sound to work Jaunty?  HDMI does not appear in my Preferences>Sound drop down menu. 64-bit Jaunty NVIDIA.

Clarification - is Post #2 a solution for Jaunty HDMI or the solution for getting HDMI to work with YouTube?

---

### Post by syzygies on 2009-12-21
bump

---

### Post by drkronic on 2009-12-23
bump bump

---

