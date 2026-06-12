---
title: "Ubuntu 10.10 Freezes Randomly"
date: 2011-02-04
forum: Desktop Environments
---

### Post by dpaulat on 2011-02-04
I have installed Ubuntu 10.10 on other machines before and have not experienced this problem.

Occasionally, the system will lock up.  They keyboard and mouse stop responding (my keyboard status lights no longer respond, but my optical mouse light is still on).  I can ssh to the machine, and it seems to work as normal.  I kill processes that are open on my desktop through ssh, (i.e., Firefox), and I notice when I switch back, I still have the same frozen image on my screen.

I have looked at the following files to determine any issues with the GPU:

/sys/kernel/debug/dri/0/i915_error_state
  - No errors
/sys/kernel/debug/dri/0/i915_wedged
  - State is 0, I'm assuming this is not wedged
/sys/kernel/debug/dri/0/i915_ringbuffer_info
  - ***Buffer is not updating

Basic software/hardware specs:

Kernel Linux 2.6.35-25-generic
GNOME 2.32.0

Memory: 2GB
Processor 0/1: Genuine Intel(R) CPU 2140 @ 1.60GHz

Running through the system test quickly doesn't show any red flags.  Does anyone have any ideas why this might be happening, or suggestions to fix this?

Thanks,
Dan

---

### Post by dpaulat on 2011-02-04
A few more pieces of information that may or may not be helpful:


[LIST]
[*]As in the post above, SSH works.  VNC server does not after a lockup.  Clients will hang on connection.
[*]USB mouse/keyboard (with KVM switch), have not tried PS/2.  This exact peripheral setup has worked on other Ubuntu 10.10 machines.
[/LIST]

---

### Post by dpaulat on 2011-02-11
I thought this might have something to do with graphics settings, so I turned the visual effects to the minimum.  I thought it worked, as I went some time without a freeze, but after some idle time, I discovered that the same problem had manifested itself.  Again, services appear to be working, but VNC and direct access to the machine do not work.

UPDATE:
I did some digging and found some interesting information in the syslog (there are many of these messages):
```
Feb  3 22:49:32 longbow kernel: [ 1440.288032] INFO: task i915:648 blocked for more than 120 seconds.
Feb  3 22:49:32 longbow kernel: [ 1440.288210] INFO: task Xorg:979 blocked for more than 120 seconds.
```It appears that this has been an issue with Intel chipsets since at least 8.04 (and not specific to Ubuntu), with numerous bugs written about the issue, and I haven't been able to find any sort of resolution.  Does anyone know any progress on this annoyance?

---

