---
title: "Laggy Ubuntu"
date: 2007-05-01
forum: Desktop Environments
---

### Post by minime72706 on 2007-05-01
Hey, I'm running Ubuntu 7.04 on a computer with the following hardware:

AMD FX-55 2.6GHz processor
2gb (4x512mb) pc3200 RAM
2x NVIDIA 6800ULTRAs in SLI
Ubuntu has a 74gb Raptor HDD to itself
base model Creative Audigy sound card

Note: the problem I'm going to outline occurred in the previous release of Ubuntu as well.

The problem is that about every five seconds my mouse will jump as if the computer was lagging. Other applications are affected as well. I've seen evidence of the lag for example in the spinning 'web page loading' symbol on the top right corner of Mozilla FIrefox.

I've monitored ... my system monitor and found that CPU usage jumps continuously between 0% and 40% continuously, even if I'm not doing anything. I have 28 processes running, and I do not see a jump in CPU usage in any of them except maybe gnome-system-monitor and a tiny one in gnome-screensaver. The spike may be too fast to be picked up this way, or its not related to the processes running. I do have screenshots of the graphs and processes lists.

Note: I do have beryl installed, but I don't believe this is causing the lag as in the previous version of Ubuntu I had the same problem without beryl installed. This is a new install and this lag wasn't happening until I turned the computer on today. After this post I am going to restart and see if it still happens.

Thanks in advance for any input.

---

### Post by minime72706 on 2007-05-01
I restarted, no change.

---

### Post by minime72706 on 2007-05-01
???

---

### Post by Ozeuss on 2007-05-01
Err.. are you monitoring all processes or just user processes?
maybe you should try to shorten the update interval in order to "catch" the culprit. other than that i really don't know...

---

### Post by minime72706 on 2007-05-02
anyone have anything helpful?

---

### Post by orb9220 on 2007-05-02
open a term and type: top and watch what is eating up cpu during lockup.

If it shows xorg then it may be a video driver issue?

Which you did not state what video driver's you are using.

Post your xorg.conf.
Post the screenshots.

These will help us to help you.

---

