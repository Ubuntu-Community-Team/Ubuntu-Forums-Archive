---
title: "palm device crashes khubd / how to restart USB subsystem?"
date: 2006-08-19
forum: Desktop Environments
---

### Post by ChrisC on 2006-08-19
I've been putting it off for 6 months because I knew it would suck, and today I'm doing it: trying to get Palm sync working on my Ubuntu Dapper installation.  Alas, my fears have proven correct.

Here's the latest problem, in sequence:
1.  Freshly booted system.
2.  lsusb shows a couple ports and one device (a flash reader)
3.  I tail /var/log/messages to watch it while I do step 4
4.  I plug my palm device into a USB port
5.  Messages in /var/log/messages indicate that the device is recognized
6.  lsusb shows the additional Palm device
7.  I press the palm device's hotsync button, intending to see what pilot-xfer thinks of it.
8.  tailed log shows that khubd has crashed
9.  lsusb gives no results -- it hangs and I have to kill the terminal
10. I have to reboot the whole system to get USB functionality back, measured by whether lsusb works.

When I attempt the device HotSync, a whole lot of stuff gets dumped to the log, including this at the beginning:

Aug 19 18:00:12 localhost kernel: [17179931.608000] usb 1-3: USB disconnect, address 4
Aug 19 18:00:12 localhost kernel: [17179931.608000] ------------[ cut here ]------------
Aug 19 18:00:12 localhost kernel: [17179931.608000] PREEMPT SMP
Aug 19 18:00:12 localhost kernel: [17179931.608000] Modules linked in: 

... some things in the middle about process, stack and call trace information (I can provide on request), and then this at the end.

Aug 19 18:00:12 localhost kernel: [17179931.608000]  <6>note: khubd[1904] exited with preempt_count 1

Any ideas?

Any way to restart the USB subsystem without rebooting the whole computer?

---

### Post by ChrisC on 2006-08-20
Anyone?  Ideas on why khubd is crashing, or how to restart the USB subsystem without rebooting the whole computer?

---

### Post by ChrisC on 2006-08-21
I'll pay $20 for any answer that moves me forward on this.  You don't even have to completely solve my problem, just move me forward.

USB system restart? 

Here's another question, related, same deal.  gnome-pilot seemed to talk to my device, since it was able to pull the Palm ID.  How can I carry that success over to jpilot?  I want to avoid Evolution at all costs, it's awful.  Of course, maybe gnome-pilot only worked once and then khubd crashed ...

---

### Post by ChrisC on 2006-08-21
I'll pay $20 for any answer that moves me forward on this.  You don't even have to completely solve my problem, just move me forward.

USB system restart? 

Here's another question, related, same deal.  gnome-pilot seemed to talk to my device, since it was able to pull the Palm ID.  How can I carry that success over to jpilot?  I want to avoid Evolution at all costs, it's awful.  Of course, maybe gnome-pilot only worked once and then khubd crashed ...

---

### Post by ChrisC on 2006-08-21
Whoops, sorry.  Net's acting funky.  Maybe I'll pay $40 :)

---

### Post by maniacmusician on 2006-08-22
you sure this shouldnt be in the hardware section? i dont know what your odds are of finding someone that knows about tihs in Desktop Support.

---

### Post by ChrisC on 2006-08-22
Thanks mm, I'll try over there.

---

