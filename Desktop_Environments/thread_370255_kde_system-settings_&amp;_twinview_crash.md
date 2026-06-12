---
title: "kde system-settings &amp; twinview crash"
date: 2007-02-25
forum: Desktop Environments
---

### Post by ^rooker on 2007-02-25
Hi, 
I thought I might try TwinView on my nVidia GeForce FX 5600 with 2 CRT monitors - and I already got it working by manually modifying my xorg.conf.

but: Now I like consistency, and KDE's "system settings / Monitor & Display" settings seemed to be unaware of my dual-screen setup. I wanted to change that. It keeps either ignoring my changes, or doing "nothing" when entering "administrative mode" or even worse: crash upon "apply".

Details:

I entered both screens (by manufacturer), applied my changes - and: nothing happened. After restarting my x-server and opening those settings again it seemed like I've never been there. :confused: 

...So I thought that maybe my manual changes confused the parser, so I restored my original xorg.conf and tried to enable dual-screen from the GUI, but 2 problems appeared:

1) When entering the administrational mode, the frame turns red (as usual) and nothing more. the frame itself stays empty.
2) After enabling the nvidia driver ("sudo nvidia-glx-config enable"), I can configure stuff in administrational mode, but applying changes gives me a crash report.


Is that dual-mode configuration of KDE still experimental? Any suggestions on how to get that GUI-frontend in-sync with my xorg.conf? 
btw: I'm one of the brave Feisty-testers, so I expect some roughness...

---

