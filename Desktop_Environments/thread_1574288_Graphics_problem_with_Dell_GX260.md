---
title: "Graphics problem with Dell GX260"
date: 2010-09-14
forum: Desktop Environments
---

### Post by matsyuf on 2010-09-14
Hullo,

I have upgraded from 8.10 to 10.04 and  blacks out as I am working. I am wondering how i can stop this from  happening.

I had 8.10 and everything was working just fine.

Any assistance will be appreciated

...

Below are my logs

Sep 13 16:18:21 Library00 kernel: [  624.436025] [drm:i915_hangcheck_elapsed] *ERROR* Hangcheck timer elapsed... GPU hung
Sep 13 16:18:21 Library00 kernel: [  624.436042] render error detected, EIR: 0x00000000
Sep 13 16:18:23 Library00 kernel: [  626.868026] [drm:i915_gem_idle] *ERROR* hardware wedged
Sep 13 16:18:23 Library00 gnome-session[1118]: WARNING: Detected that screensaver has left the bus
Sep 13 16:18:24 Library00 gdm-simple-slave[1424]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Sep 13 16:18:24 Library00 acpid: client 819[0:0] has disconnected
Sep 13 16:18:24 Library00 acpid: client connected from 1440[0:0]
Sep 13 16:18:24 Library00 acpid: 1 client rule loaded
Sep 13 16:18:24 Library00 pulseaudio[1438]: pid.c: Stale PID file, overwriting.
Sep 13 16:18:25 Library00 pulseaudio[1438]: main.c: Unable to contact  D-Bus: org.freedesktop.DBus.Error.NoServer: Failed to connect to socket  /tmp/dbus-nSv7Hc3upt: Connection refused
Sep 13 16:18:25 Library00 kernel: [  628.833092] [drm:i915_gem_entervt_ioctl] *ERROR* Reenabling wedged hardware, good luck
Sep 13 16:18:26 Library00 kernel: [  629.148030] [drm:i915_hangcheck_elapsed] *ERROR* Hangcheck timer elapsed... GPU hung
Sep 13 16:18:26 Library00 kernel: [  629.148042] render error detected, EIR: 0x00000000
Sep 13 16:18:26 Library00 kernel: [  629.148935]  [drm:i915_do_wait_request] *ERROR* i915_do_wait_request returns -5  (awaiting 49169 at 49165)

---

### Post by dino99 on 2010-09-14
old xorg.conf often break the graphic system, as now kernel deal directly with X, you can delete xorg.conf

sudo rm -f /etc/X11/xorg.conf

then reboot and check driver activation: system admin additionals drivers

*** you can watch the Dell subforum to know issue about this model (if any)

---

### Post by cheruvim on 2010-11-23
Hey, thanks for taking the time to answer..

I had the same problem.. At first Karmic Koala would have the screen freeze up and now LTS 10.04 would go blank

I looked at xorg.conf, looked kosher, however, I moved out of the /etc/X11 dir before restarting (I logged in via ssh shell from another machine). I restarted and it booted fineI selected the System -> administrator -> Hardware Drivers panel and it didn't find any 3 rd party drivers... However I wasn't sure if that's what you meant by "additional drivers" 


So far I haven't encountered the problem, HOwever we'll see.
Thanks,
Carl.

---

