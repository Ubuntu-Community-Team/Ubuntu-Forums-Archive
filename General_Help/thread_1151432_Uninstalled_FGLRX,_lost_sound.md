---
title: "Uninstalled FGLRX, lost sound"
date: 2009-05-06
forum: General Help
---

### Post by darundal on 2009-05-06
I recently tried to see if Jaunty would play nice with my x850 pro. After switching to the FGLRX drivers, my system would freeze during boot (some horrid issue with X). I attempted to fix this by switching back to my integrated intel graphics, however the problems persisted. I removed every FGLRX related package from my system, which fixed my video troubles. However, pulse now doesn't work. Manually starting pulse from a terminal yields this:

```
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
N: main.c: Called SUID root and real-time and/or high-priority scheduling was requested in the configuration. However, we lack the necessary privileges:
N: main.c: We are not in group 'pulse-rt', PolicyKit refuse to grant us the requested privileges and we have no increase RLIMIT_NICE/RLIMIT_RTPRIO resource limits.
N: main.c: For enabling real-time/high-priority scheduling please acquire the appropriate PolicyKit privileges, or become a member of 'pulse-rt', or increase the RLIMIT_NICE/RLIMIT_RTPRIO resource limits for this user.
W: pid.c: Stale PID file, overwriting.
W: alsa-util.c: Cannot find fallback mixer control "PCM" or mixer control is no combination of switch/volume.
E: alsa-util.c: Error opening PCM device hw:0: Device or resource busy
E: module.c: Failed to load  module "module-alsa-source" (argument: "device_id=0 source_name=alsa_input.pci_1102_4_sound_card_0_alsa_capture_0 tsched=0"): initialization failed.
```


Anyone have any ideas how to fix this?

---

