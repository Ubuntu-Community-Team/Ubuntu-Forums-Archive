---
title: "blank screen after resume"
date: 2009-04-12
forum: General Help
---

### Post by xiaoyihf on 2009-04-12
Occasionally, I got blank screen when I resume my laptop after I suspend it by close the lid of my laptop.

I am quite sure this is caused by the following error message:

Apr 12 10:52:39 ubuntu pulseaudio[5428]: ltdl-bind-now.c: Failed to find original dlopen loader.
Apr 12 10:52:39 ubuntu pulseaudio[5431]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Apr 12 10:52:39 ubuntu pulseaudio[5431]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Apr 12 10:52:40 ubuntu pulseaudio[5431]: alsa-util.c: Cannot find fallback mixer control "Mic".
Apr 12 10:52:56 ubuntu pulseaudio[5431]: module-x11-xsmp.c: X11 session manager not running.
Apr 12 10:52:56 ubuntu pulseaudio[5431]: module.c: Failed to load  module "module-x11-xsmp" (argument: ""): initialization failed.

---

### Post by xiaoyihf on 2009-05-23
After I upgrade the system to jaunty, the problem is gone!!!!!!!!!!!:p:popcorn::D:o:)

---

