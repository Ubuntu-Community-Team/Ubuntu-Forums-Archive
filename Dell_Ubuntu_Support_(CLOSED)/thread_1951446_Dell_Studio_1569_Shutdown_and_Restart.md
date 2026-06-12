---
title: "Dell Studio 1569 Shutdown and Restart"
date: 2012-04-02
forum: Dell Ubuntu Support (CLOSED)
---

### Post by CSNate on 2012-04-02
Hello all, I did find a similar thread on this but the thread was too general and really did not seem to have enough information.

So I have a Dell Studio 1569 and I am running Ubuntu 11.10 64-bit.  The problem I am having at this point is that the computer does not want to shutdown or restart.  When I choose to shutdown, I get a message that says Will now halt and the computer just sits there.  If you wait long enough, the kernel reports that it detected a CPU stall.

The same thing happens when I restart, except that it says Will now restart.

I have both the Ubuntu Kernel installed and the Liquorix kernel, both have this same issue.  I have been searching, but to no avail.  Help is appreciated :)  I'm not sure if this heps at all, but I am using SELinux.  The problem continued with and without it.

Liquorix Kernel
```
Linux glados 3.2.0-13.dmz.2-liquorix-amd64 #1 ZEN SMP PREEMPT Tue Mar 27 21:45:43 CDT 2012 x86_64 x86_64 x86_64 GNU/Linux

```Generic Kernel
```
Linux glados 3.0.0-17-generic #30-Ubuntu SMP Thu Mar 8 20:45:39 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
```

Help is appreciated.

---

### Post by CSNate on 2012-04-03
Update:

I've noticed that during the shutdown\restart procedure, when the computer does not shutdown, Asking all Processes to terminate fails...  Any idea on how to debug this issue?

---

### Post by rfry11 on 2012-04-17
I have the same issue on 11.10 Oneiric and on 12.04 Precise Beta on my Dell Studio 1569.

---

### Post by lisanels47 on 2012-04-18
I've seen this as well on my Dell 1545 Inspiron.  I think that's why the put the Windows warning stickers on the computers!

I'm running 12.04 fine, and 11.10 was running good too.  So I believe this issue is lurking out there to hit more of us again.  I know if you logon with CTR-ALT-F2, and have a session open there, the system will refuse to shutdown.  I use 'init 6' as root to force them to restart.

---

