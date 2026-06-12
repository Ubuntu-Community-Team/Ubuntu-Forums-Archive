---
title: "black/flickering screen after closing lid"
date: 2015-11-06
forum: Desktop Environments
---

### Post by Deling_Ren on 2015-11-06
I have seen some mentioning of this issue and it sounds like this has been fixed some time in 14. However I'm seeing it on 15.10 on a fresh installation. Changing the light locker seems to have made it worse. Instead of going blank, it's now flickering. Killing X altogether from a console solves the issue. After that, it won't happen till it reboots. 

When the screen flickers, I get a message on the console:

[drm:intel_pipe_config_compare [i915]] *ERROR* mismatch in gmch_pfit.pgm_ratios (expected 1409373102, found 1409307648)

It sounds like a video driver problem. I have run the vanilla Ubuntu (unity?) on this machine and it worked fine with closing lid. The machine is a Lenovo x60. The graphics card is Intel GMA 950, I believe.

---

