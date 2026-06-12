---
title: "No menu's when booting on battery"
date: 2010-11-16
forum: Desktop Environments
---

### Post by ijntema on 2010-11-16
Hi
I have a stock Ubuntu 10.10 on a Medion Akoya E1315. All works fine when laptop is plugged into the mains.
When I bootup on bsttery, I can log-on, but then I only get a partial desktop (only lower part with trash, no menu's). System is stuck....

Any ideas?
Cheers
Hans

---

### Post by ijntema on 2010-12-05
Hi

Does no one have a clue? I have looked at the logs, but no clue where to look (for this issue). I am pretty experienced with Linux, but clueless.

Problem defeats the usefullness of a laptop/netbook.....

Today i did get a full desktop, mouse moves, but I cannot not click on anything. Pressing power button did not give me the shutdown menu.

Everything works fine at logon screen. Everything works fine with power plugged in. Everything works fine if I remove power after logon....

Cheers
Hans

---

### Post by sikander3786 on 2010-12-05
I don't have an absolute solution here.

But I would recommend to test your system by booting from an Ubuntu Live CD/USB while power is not plugged in and see if it gives the same problem on the Live media as well or it is a problem with your install/configuration only.

---

### Post by ijntema on 2010-12-21
Removing pm-utils (and acpi) fixed the problem...but what do I lose? Powermanagement?

Cheers
Hans

---

