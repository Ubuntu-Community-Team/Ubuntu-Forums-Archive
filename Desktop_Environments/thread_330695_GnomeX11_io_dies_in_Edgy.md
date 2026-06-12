---
title: "Gnome/X11 i/o dies in Edgy"
date: 2007-01-03
forum: Desktop Environments
---

### Post by reidmefirst on 2007-01-03
I updated my Dapper install to Edgy about two weeks ago.  It was running fine (24x7 compiling things, web browsing, reading email, etc) until this morning, when I decided to play with the Xen hypervisor + xen dom0 kernel.  I just installed the normal xen-hypervisor-3.0-i386 and xen-image-xen0-2.6.17-6-generic-xen0 packages, ran mkinitramfs to generate a new ramfs for xen and updated grub's menu.lst  (as per the instructions at [https://help.ubuntu.com/community/XenVirtualMachine/XenOnUbuntuEdgy](https://help.ubuntu.com/community/XenVirtualMachine/XenOnUbuntuEdgy) ).  So far, I am only running the Edgy dom0 under Xen.

When I rebooted and everything seemed fine for a while.  After maybe 30 minutes or so, my gnome session froze up.  I noticed that a keystroke or two got dropped, then more and more, and the mouse stopped responding to clicking.  From the initial keystroke drop until it became completely unresponsive was quite a rapid process, within a few seconds.  I then ctrl-alt-backspace'd and X/gdm restarted just fine, but the problem is recurring.

I started tailing my logfiles in the background to see if anything weird was happening when the freezing occurred.  It seems that every time the freeze happened, NTP had just synchronized my clock with the servers (I have two timeservers defined in my config file):

Jan  3 11:03:37 krwightm-desktop ntpd[5016]: reply from ntp1: negative delay -0.000030
Jan  3 11:04:01 krwightm-desktop ntpd[5016]: reply from ntp2: negative delay -0.000033

(Less than one second later, my desktop experiences freezing problems, repeat similar situation 3 times).

I'm not sure if correlation really equates to causation here, but it's the best clue that I have so far.  A few minutes after killing the Xserver the last time, I saw this pop up in syslog:

Jan  3 11:35:49 krwightm-desktop ntpd[5016]: ntp engine exiting
Jan  3 11:35:49 krwightm-desktop ntpd[5015]: dispatch_imsg in main: pipe closed
Jan  3 11:35:49 krwightm-desktop ntpd[5015]: Lost child: child exited
Jan  3 11:35:49 krwightm-desktop ntpd[5015]: Terminating

Since then, the problem hasn't re-occurred, lending some possible weight to my theory that time synchronization is causing the problem.  I'm skeptical though, it seems odd that the xserver or gnome should care if the system time skews by such slight margins now and then.  Has anyone else had this kind of problem, with or without Xen and openntpd running?  Or can anyone help me to track down the problem further?  Anything else that I should maybe look into?

Thanks,
Reid

---

### Post by tschwinge on 2007-01-27
The ntpd problem may (very likely) be the same issue I reported here: [http://bugs.debian.org/380737]("http://bugs.debian.org/380737").

Did you already investigate further?

---

### Post by reidmefirst on 2007-01-30
Cool, thanks.  I hadn't looked.  This is probably the same issue, as I'm getting as I see only negative clock skews using xen + linux-dom0 as well.  Curious, it doesn't look like anyone else in that thread has experienced the weird I/O issues that I have, though...

---

### Post by alexgutteridge on 2007-03-16
Just noticed the same thing here on a fresh Edgy install. It's been running for a few days fine now, but I've noticed a few key strokes getting lost and a slow freeze up of mouse clicks/movement etc...

No obvious problems with ntpd in my logs, does anyone have any other ideas? It's pretty irritating...

---

