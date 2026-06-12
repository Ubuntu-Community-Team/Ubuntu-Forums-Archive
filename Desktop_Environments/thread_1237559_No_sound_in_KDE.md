---
title: "No sound in KDE"
date: 2009-08-11
forum: Desktop Environments
---

### Post by sookun on 2009-08-11
hello there, i have ubuntu 9.04 recently added KDE but unlike gnome i dont get sound in KDE when i run music or videos..but the logging gingle works..weird
sudo kcmshell arts
Error: "/tmp/ksocket-veesham" is owned by uid 1000 instead of uid 0.
Error: "/tmp/ksocket-veesham" is owned by uid 1000 instead of uid 0.
kbuildsycoca running...
Error: "/var/tmp/kdecache-veesham" is owned by uid 1000 instead of uid 0.
Reusing existing ksycoca
Error: "/var/tmp/kdecache-veesham" is owned by uid 1000 instead of uid 0.
Error: "/var/tmp/kdecache-veesham" is owned by uid 1000 instead of uid 0.
Error: "/var/tmp/kdecache-veesham" is owned by uid 1000 instead of uid 0.

sudo kmix
[sudo] password for veesham:             
Error: "/var/tmp/kdecache-veesham" is owned by uid 1000 instead of uid 0.
kmix(6385) Mixer::setGlobalMaster: Mixer::setGlobalMaster() card= "ALSA::HDA_Intel:1"  control= "PCM:0"
E: core-util.c: Home directory /home/veesham not ours.
kmix(6385) Mixer::openIfValid: Mixer::open() detected master:  "PCM:0"

in an another post i saw some1 changed the master channel in the alsamixer and it seemed to be working but how to do that??

---

### Post by Raboch on 2009-08-11
Just a hunch, but I used to have sound problems that I fixed by going into System Settings, multimedia, and going through all the listings in the "exit of audio" or however it's phrased in English and selecting PulseAudio and clicking the "prefer" button to get it to the top of the list. Since then the sound has worked fine all around. Also if by chance you can't hear while using headphones you can right click the sound icon and bring up the mixer window and unmute surround.

---

