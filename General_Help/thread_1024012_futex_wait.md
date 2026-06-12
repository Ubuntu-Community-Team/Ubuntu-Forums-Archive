---
title: "futex wait"
date: 2008-12-28
forum: General Help
---

### Post by wall0645 on 2008-12-28
So I just put Ubuntu 8.10 on my desktop (been using 8.04 on my laptop for a while now), and it's pretty nice. The only problem is that programs often freeze for no apparent reason. In the System Monitor their "Waiting Channel" is shown as "futex_wait".

Does this mean something specific? i.e., can this be fixed? Is this an 8.10 issue (should I just use 8.04?)?

I just can't tell if this is a problem with the OS or a problem with my computer (hardware) itself, because I haven't installed hardly anything yet. I have only downloaded the 200+ updates, gotten adobe flash v10, and activated an nvidia driver.

Thanks for the help in advance!

---

### Post by Killerah on 2009-01-11
I'm having the same problem, if someone knows how to fix the issue I would greatly appreciate it.

---

### Post by teddks on 2009-01-11
That means the program is a multi-threaded application waiting on a futex. If it's frozen, it's gotten deadlocked. You should report bugs for those programs, and post which ones are crashing here so that we can try to reproduce them. :)

---

### Post by mlissner on 2009-01-16
That was my analysis too, but it seems to be happening to a lot of different programs. I went into System Monitor, turned on the column for Waiting Channel, and then showed all processes, and had several that were stuck at the futex_wait, including Firefox, Gnome-do, eog, eclipse, python, and gvfs-fuse-daemon.

I don't think it's all these programs that are causing the problem since they never did before - I think it's a kernel bug. 

I did see on [this pos]("http://ubuntuforums.org/showthread.php?p=6144521")t that turning off accessibility seems to fix their futex problem. I've tried that, but it's too soon to see if it actually fixes the problem.

---

### Post by Andrew_P on 2010-09-28
> **mlissner said:**
> I did see on [this pos]("http://ubuntuforums.org/showthread.php?p=6144521")t that turning off accessibility seems to fix their futex problem. I've tried that, but it's too soon to see if it actually fixes the problem.

I'm seeing the futex_wait hang problem on an Ubuntu 8.10 machine that doesn't have Assistive Technologies enabled.  Most recently it seems to be happening with Adobe Reader 9.  It may have been doing so all along, but I only learned about futex_wait today.  When it happens, Adobe Reader can't be stopped with the End Process button in System Monitor; the only way to stop it is to Kill it.

---

### Post by Andrew_P on 2011-07-08
Since migrating to 10.04.1 LTS, I rarely encountered futex_wait_queue_me hangs until in early 2011 I installed SeaMonkey 2.0, the successor to Netscape Suite and Mozilla Suite.  I rarely use Firefox, the default browser that comes with Ubuntu, so I don't have much real-world data on its behavior.  SeaMonkey 2 was revamped to use the Gecko rendering engine from Firefox 3.5.4, and shares who-knows-what code with the latter.

Of late, I've noticed SeaMonkey 2.0.14 hanging frequently with futex_wait_queue_me in the Wait Channel.  The only way to get it back is to End or Kill it with System Monitor.  Sometimes it even causes the entire system to lock up or crash -- something a user program on Linux should never be able to do.

**It gets weirder**:confused:
SeaMonkey 2.0.14 will hang with futex_wait_queue_me during startup, before it even can open a window on the desktop, a few seconds after startup, or a few minutes after startup while viewing pages that never caused problems with release 1.1.18, the last pure-Mozilla code version.  Firefox 3.6.17 and 3.6.18 behaves the same.  It's so bad that the suite has become almost useless, as it will randomly hang while viewing a Web page or composing an e-mail message. *However*, I'm finding that if the suite is started just after midnight, it will run for 11+ hours flawlessly, never experiencing a futex_wait_queue_me hang.  I don't know if this time-of-day dependency is similar with applications other than SeaMonkey and Firefox, but it would be good if users could run tests with their problematic programs during all times of the day and see what happens.

During times when both SeaMonkey and Firefox are balky, I use the Opera browser, which to-date has never shown a tendency to hang with futex_wait_queue_me.  This tells me that the problem is most likely in the user programs, not the Linux kernel.

---

