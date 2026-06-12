---
title: "xserver crashes after apt-get upgrade"
date: 2009-01-23
forum: General Help
---

### Post by stephan0h on 2009-01-23
so finally i had the time to upgrade again on my acer aspire one. all worked well. the system requested me to restart the system, which i did, when it came up again i logged in to xfce - xserver started up only to close down immediately. and this is what it keeps doing since then. so i have no graphical interface anymore. system is xubuntu intrepid. any clues?

thanks,
stephan

---

### Post by stephan0h on 2009-01-25
some more information on this!

i found this in syslog:

Jan 23 16:21:07 stephan-laptop nm-system-settings: Adding default connection 'Auto eth0' for /org/freedesktop/Hal/devices/net_00_1e_68_cd_9d_02
Jan 23 16:21:07 stephan-laptop kernel: [   63.481381] [drm] Initialized drm 1.1.0 20060810
Jan 23 16:21:07 stephan-laptop kernel: [   63.503093] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
Jan 23 16:21:07 stephan-laptop kernel: [   63.503126] pci 0000:00:02.0: setting latency timer to 64
Jan 23 16:21:07 stephan-laptop kernel: [   63.503807] [drm] Initialized i915 1.6.0 20060119 on minor 0
Jan 23 16:21:08 stephan-laptop kernel: [   63.793681] mtrr: no more MTRRs available
Jan 23 16:21:59 stephan-laptop kernel: [  115.493833] xfce4-session[5942]: segfault at b71612f8 ip b71612f8 sp bf98b9f0 error 4 in xfce4-session.mo[b7167000+4000]
Jan 23 16:22:01 stephan-laptop kernel: [  117.122454] mtrr: no MTRR for 40000000,10000000 found
Jan 23 16:22:02 stephan-laptop acpid: client connected from 6262[0:0] 
Jan 23 16:22:04 stephan-laptop kernel: [  119.922100] mtrr: no more MTRRs available
Jan 23 16:22:35 stephan-laptop kernel: [  151.016022] xfce4-session[6372]: segfault at b72562f8 ip b72562f8 sp bfe80b20 error 4 in xfce4-session.mo[b725c000+4000]

so clearly, there's a segfault happening in xfce4.

any ideas, please?

thanks,
stephan

---

