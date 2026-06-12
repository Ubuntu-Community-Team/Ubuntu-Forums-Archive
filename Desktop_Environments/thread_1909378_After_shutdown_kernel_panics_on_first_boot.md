---
title: "After shutdown: kernel panics on first boot"
date: 2012-01-15
forum: Desktop Environments
---

### Post by Triptol on 2012-01-15
My HTPC is running on 11.10 64 bit. It has one of those Intel multimedia boards: DH67GD.

I use bios wakeup to schedule my recordings and mythtv takes care of setting that and shutting down the system (to save some energy).

Now for some reason if the system has been running for some time (approximately 15 minutes) and shuts down, the kernel always panics the next time the system starts. I have configured the system to reboot after a kernel oops and that works correctly. So after the oops my system reboots and this time it always boots correctly: effectively doubling my boot time.

Now the problem is that I have no clue how to intercept a kernel oops during boot. I am not able to read all the information on my tv screen and there are no logs that describe the oops. Would any of you guys know how to log this information to a filesystem, so I can at least find what is causing the kernel to oops?

Putting my hopes up very high here: maybe you guys have seen it before and know how to fix this one?

Happy to provide any additional information.

---

### Post by Triptol on 2012-01-29
Now running on 3.0.0-15 and still having the same problems. No one else here seeing this?

---

### Post by drs305 on 2012-01-29
Disclaimer: I'm no log expert and I probably can't help much but I'm interested in the thread.

If you look at the Log File viewer via Dash it only shows the current dmesg contents. Of course it would reflect the latest (successful) boot. 

Have you looked at the previous one (/var/log/dmesg0) to see if it sheds any light on your problem?

---

