---
title: "Hard Lookups in Jaunty Jackalope"
date: 2009-05-16
forum: General Help
---

### Post by downfall8 on 2009-05-16
I keep getting hard lock ups, here are the last few lines from syslog:

May 16 17:22:05 andrew-desktop NetworkManager: <info>  (eth1): device state change: 7 -> 8 
May 16 17:22:05 andrew-desktop NetworkManager: <info>  Policy set 'Auto eth1' (eth1) as default for routing and DNS. 
May 16 17:22:05 andrew-desktop NetworkManager: <info>  Activation (eth1) successful, device activated. 
May 16 17:22:05 andrew-desktop NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) complete. 
May 16 17:22:07 andrew-desktop pulseaudio[3521]: module-x11-xsmp.c: X11 session manager not running.
May 16 17:22:08 andrew-desktop pulseaudio[3521]: module.c: Failed to load  module "module-x11-xsmp" (argument: ""): initialization failed.
May 16 17:22:10 andrew-desktop ntpdate[3622]: no server suitable for synchronization found
May 16 17:22:11 andrew-desktop kernel: [   34.384006] eth1: no IPv6 routers present


Any help would be greatly appreciated, I'm getting rather frustrated.

---

### Post by mkvnmtr on 2009-05-16
I had the same problem a time or two but I was never sure if it was my fault. I delete a lot of stuff from a standard Ubuntu and then install a good bit. I thought maybe bugs in the new upgrade a d maybe it will straighten out. Hasn't happened in a few days but I never saw an update that looked like it was related.

---

### Post by downfall8 on 2009-05-21
Still getting these hard lockups.  The last time there was something new at the end of syslog:

(   cd / && run-parts --report /etc/cron.hourly)

Anybody have any ideas what might be causing this, my hardware is brand new.

---

### Post by hanzomon4 on 2009-05-22
Do you have the rt kernel installed?

---

### Post by downfall8 on 2009-05-22
> **hanzomon4 said:**
> Do you have the rt kernel installed?

No, should it be?

---

### Post by hanzomon4 on 2009-05-22
No... but I installed it for audio work and it caused Hard random lockups.. I just booted into a different kernel

---

