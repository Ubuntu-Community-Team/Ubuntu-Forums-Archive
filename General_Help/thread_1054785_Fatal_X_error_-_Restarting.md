---
title: "Fatal X error - Restarting"
date: 2009-01-30
forum: General Help
---

### Post by Birk on 2009-01-30
Hi,
My computer keeps on crashing lately without any warning, I don't know what exactly triggers it, but it might have something to do with amarok (my mp3 player).
The computer does not crash completely, but just restarts the x-server. This happened for example last time I tried to open amarok. The only program running besides this was matlab, I mean actively started by me.
Following is the syslog entry for this event (I hope this is the right thing, I don't much about this):
Jan 30 00:01:01 birk-laptop -- MARK --
Jan 30 00:14:22 birk-laptop gdm[5989]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0 
Jan 30 00:14:38 birk-laptop pulseaudio[11160]: pid.c: Stale PID file, overwriting.
Jan 30 00:14:42 birk-laptop NetworkManager: <info>  Updating allowed wireless network lists. 
Jan 30 00:14:44 birk-laptop anacron[11366]: Anacron 2.3 started on 2009-01-30
Jan 30 00:14:44 birk-laptop kernel: [ 3104.275355] CPU0 attaching NULL sched-domain.
Jan 30 00:14:44 birk-laptop kernel: [ 3104.275366] CPU1 attaching NULL sched-domain.
Jan 30 00:14:44 birk-laptop kernel: [ 3104.295172] CPU0 attaching sched-domain:
Jan 30 00:14:44 birk-laptop kernel: [ 3104.295178]  domain 0: span 03
Jan 30 00:14:44 birk-laptop kernel: [ 3104.295180]   groups: 01 02
Jan 30 00:14:44 birk-laptop kernel: [ 3104.295185] CPU1 attaching sched-domain:
Jan 30 00:14:44 birk-laptop kernel: [ 3104.295188]  domain 0: span 03
Jan 30 00:14:44 birk-laptop kernel: [ 3104.295190]   groups: 02 01
Jan 30 00:14:44 birk-laptop anacron[11366]: Will run job `cron.daily' in 5 min.
Jan 30 00:14:44 birk-laptop anacron[11366]: Jobs will be executed sequentially
Jan 30 00:16:58 birk-laptop gdm[11054]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0 
Jan 30 00:17:01 birk-laptop /USR/SBIN/CRON[12107]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jan 30 00:17:11 birk-laptop pulseaudio[12204]: pid.c: Stale PID file, overwriting.
Jan 30 00:17:12 birk-laptop NetworkManager: <info>  Updating allowed wireless network lists. 
Jan 30 00:17:13 birk-laptop kernel: [ 3183.274132] CPU0 attaching NULL sched-domain.
Jan 30 00:17:13 birk-laptop kernel: [ 3183.274139] CPU1 attaching NULL sched-domain.
Jan 30 00:17:13 birk-laptop kernel: [ 3183.290417] CPU0 attaching sched-domain:
Jan 30 00:17:13 birk-laptop kernel: [ 3183.290422]  domain 0: span 03
Jan 30 00:17:13 birk-laptop kernel: [ 3183.290424]   groups: 01 02
Jan 30 00:17:13 birk-laptop kernel: [ 3183.290427] CPU1 attaching sched-domain:
Jan 30 00:17:13 birk-laptop kernel: [ 3183.290428]  domain 0: span 03
Jan 30 00:17:13 birk-laptop kernel: [ 3183.290430]   groups: 02 01

Thank you very much
Birk

---

