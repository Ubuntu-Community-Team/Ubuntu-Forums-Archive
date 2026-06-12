---
title: "Monitor all green after switching between inputs"
date: 2020-09-28
forum: Desktop Environments
---

### Post by jdderby2 on 2020-09-28
I have 2 dual port monitors, one port on each monitor is connected to a work PC, and one port on each monitor is connect to my Ubuntu 20.04 machine.  Occasionally the when I try to switch back to the Ubuntu side the monitors are all green.  I can't get to a login screen or anything and ultimately have to force a reboot.  I am looking for some suggestions on where to start troubleshooting.

---

### Post by jdderby2 on 2020-09-28
I was able to find a little more information:

Sep 28 16:00:06 tux kernel: snd_hda_intel 0000:0a:00.1: Refused to change power state, currently in D0
Sep 28 16:00:09 tux kernel: [drm:amdgpu_job_timedout [amdgpu]] *ERROR* ring gfx_0.0.0 timeout, signaled seq=7506282, emitted seq=7506284
Sep 28 16:00:09 tux kernel: [drm:amdgpu_job_timedout [amdgpu]] *ERROR* Process information: process Xorg pid 1755 thread Xorg:cs0 pid 1757
Sep 28 16:00:09 tux kernel: [drm] GPU recovery disabled.
Sep 28 16:00:24 tux gsd-xsettings[2136]: Failed to get current display configuration state: Timeout was reached

---

