---
title: "Ubuntu 18.04 hangs on shutdown."
date: 2018-05-13
forum: Desktop Environments
---

### Post by cougar1622 on 2018-05-13
just switched from Mint 18.3 and had the same issue.  Now running 18.04 and still having issue shutting down.  Restart is fine but shutdown hangs.  
This is on a Alienware Aurora R6 GTX1080ti i7-1770k.

I'm not completely new to linux but not the greatest at this either.

---

### Post by dino99 on 2018-05-15
journalct should help you find the reason ):P

Probably an old setting left behind, try cleaning the system via 'gtkorphan' & 'bleachbit' (as root, carefully select options)

---

### Post by cougar1622 on 2018-05-16
this is what i get at the end of the output.  and this is a clean install.  Just installed 4 days ago.

May 14 22:43:00 brandon-Alienware-Aurora-R6 systemd[1]: Starting Power-Off...
May 14 22:43:00 brandon-Alienware-Aurora-R6 systemd[1]: Shutting down.
May 14 22:43:00 brandon-Alienware-Aurora-R6 kernel: systemd-shutdow: 39 output lines suppressed due to ratelimiting
May 14 22:43:00 brandon-Alienware-Aurora-R6 systemd-shutdown[1]: Syncing filesystems and block devices.
May 14 22:43:00 brandon-Alienware-Aurora-R6 systemd-shutdown[1]: Sending SIGTERM to remaining processes...
May 14 22:43:00 brandon-Alienware-Aurora-R6 systemd-journald[323]: Journal stopped


Is there a way to see whats going wrong after that.  I took a pic of the screen if that may help.

---

