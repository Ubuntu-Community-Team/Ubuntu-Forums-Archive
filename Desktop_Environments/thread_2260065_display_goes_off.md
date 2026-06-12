---
title: "display goes off"
date: 2015-01-09
forum: Desktop Environments
---

### Post by vs-punn on 2015-01-09
Ubuntu 14.04
Many times, while working, the display of my laptop goes off, and the system needs to be restarted.

this happens, while working on any files, word, html or viewing video. At around 10.53, the display went off. the syslog at that time is:
```

Jan  9 10:28:31 punnvs AptDaemon: INFO: Quitting was requested
Jan  9 10:54:17 punnvs kernel: [ 3128.004043] [drm] stuck on render ring
Jan  9 10:54:17 punnvs kernel: [ 3128.004053] [drm] GPU crash dump saved to /sys/class/drm/card0/error
Jan  9 10:54:17 punnvs kernel: [ 3128.004056] [drm] GPU hangs can indicate a bug anywhere in the entire gfx stack, including userspace.
Jan  9 10:54:17 punnvs kernel: [ 3128.004058] [drm] Please file a _new_ bug report on bugs.freedesktop.org against DRI -> DRM/Intel
Jan  9 10:54:17 punnvs kernel: [ 3128.004060] [drm] drm/i915 developers can then reassign to the right component if it's not a kernel issue.
Jan  9 10:54:17 punnvs kernel: [ 3128.004063] [drm] The gpu crash dump is required to analyze gpu hangs, so please always attach it.
Jan  9 10:54:17 punnvs kernel: [ 3128.005404] [drm:i915_set_reset_status] *ERROR* render ring hung inside bo (0x2c5e000 ctx 0) at 0x2c5f14c
Jan  9 10:54:18 punnvs kernel: [ 3128.512080] [drm:i915_reset] *ERROR* Failed to reset chip.
Jan  9 10:54:21 punnvs kernel: [ 3132.425337] Watchdog[3722]: segfault at 0 ip b638e07f sp afcc8cc0 error 6 in chrome[b2227000+5537000]
Jan  9 10:54:54 punnvs rsyslogd: [origin software="rsyslogd" swVersion="7.4.4" x-pid="399" x-info="http://www.rsyslog.com"] start
Jan  9 10:54:54 punnvs rsyslogd: rsyslogd's groupid changed to 104
Jan  9 10:54:54 punnvs rsyslogd: rsyslogd's userid changed to 101
Jan  9 10:54:54 punnvs kernel: [    0.000000] Initializing cgroup subsys cpuset
Jan  9 10:54:54 punnvs kernel: [    0.000000] Initializing cgroup subsys cpu
Jan  9 10:54:54 punnvs kernel: [    0.000000] Initializing cgroup subsys cpuacct
Jan  9 10:54:54 punnvs kernel: [    0.000000] Linux version 3.13.0-43-generic (buildd@akateko) (gcc version 4.8.2 (Ubuntu 4.8.2-19ubuntu1) ) #72-Ubuntu SMP Mon Dec 8 19:35:44 UTC 2014 (Ubuntu 3.13.0-43.72-generic 3.13.11.11)
Jan  9 10:54:54 punnvs kernel: [    0.000000] KERNEL supported cpus:
Jan  9 10:54:54 punnvs kernel: [    0.000000]   Intel GenuineIntel
Jan  9 10:54:54 punnvs kernel: [    0.000000]   AMD AuthenticAMD
Jan  9 10:54:54 punnvs kernel: [    0.000000]   NSC Geode by NSC
Jan  9 10:54:54 punnvs kernel: [    0.000000]   Cyrix CyrixInstead
Jan  9 10:54:54 punnvs kernel: [    0.000000]   Centaur CentaurHauls
Jan  9 10:54:54 punnvs kernel: [    0.000000]   Transmeta GenuineTMx86
Jan  9 10:54:54 punnvs kernel: [    0.000000]   Transmeta TransmetaCPU
Jan  9 10:54:54 punnvs kernel: [    0.000000]   UMC UMC UMC UMC
Jan  9 10:54:54 punnvs kernel: [    0.000000] e820: BIOS-provided physical RAM map:
Jan  9 10:54:54 punnvs kernel: [    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009f7ff] usable
Jan  9 10:54:54 punnvs kernel: [    0.000000] BIOS-e820: [mem 0x000000000009f800-0x000000000009ffff] reserved
Jan  9 10:54:54 punnvs kernel: [    0.000000] BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved
Jan  9 10:54:54 punnvs kernel: [    0.000000] BIOS-e820: [mem 0x0000000000100000-0x000000005f6cffff] usable
Jan  9 10:54:54 punnvs kernel: [    0.000000] BIOS-e820: [mem 0x000000005f6d0000-0x000000005f6defff] ACPI NVS
Jan  9 10:54:54 punnvs kernel: [    0.000000] BIOS-e820: [mem 0x000000005f6df000-0x000000005fffffff] reserved
Jan  9 10:54:54 punnvs kernel: [    0.000000] BIOS-e820: [mem 0x00000000e0000000-0x00000000efffffff] reserved
Jan  9 10:54:54 punnvs kernel: [    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec0ffff] reserved
```

---

### Post by kerry_s on 2015-01-09
it looks like your video driver is crashing, recall what you was doing at the time?

---

