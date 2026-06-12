---
title: "Sound popping and hissing x("
date: 2009-06-23
forum: General Help
---

### Post by kalmahlk on 2009-06-23
This only happens after a while, but if you listen to say a Rhythmbox playlist, after about 30mins it starts to quietly start popping and fizzing, and gets worse until I restart the machine. Now I have heard bad things about PulseAudio, or at least the PulseAudio Ubuntu uses, so this maybe the issue, and if not, what could it be?

---

### Post by hibliss on 2009-06-23
What version of Pulseaudio are you using? 0.9.14 has known issues, and upgrading to 0.9.15 solved a lot of issues for me, and made Stereo Bluetooth work great (with the help of Bluemon).

Here is the ppa for the latest Pulseaudio release -- [https://launchpad.net/~themuso/+archive/ppa]("https://launchpad.net/~themuso/+archive/ppa")

If you have issues with it, you cvan simply remove that ppa as a software source, remove pulseaudio through Synaptic, and reinstall.

---

