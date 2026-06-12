---
title: "Booting pauses for 40 seconds at &quot;Kinit: No resume image, doing normal boot&quot;"
date: 2009-02-16
forum: General Help
---

### Post by potatan on 2009-02-16
Hi,

When booting I get the splash screen with the progress bar but it stops for around 40-60 seconds, then carries on as normal.  Whilst it is stopped, the console in Alt-F1, says:

Kinit: No resume image, doing normal boot...

and then, 40 seconds later it carries on booting.  A couple of things to note:

1. I've searched all over the place, but most people seem to be having a problem where the boot sequence just hangs, or they have to start X manually etc.  This is not the problem for me, as booting continues as normal after the delay

2. This is a desktop machine, and I never use "Suspend", "Hibernate", or hit the power button.  I *always* shutdown using the option to shut down

So I'm not sure why it's hanging (or more correctly, pausing) at that point in the boot process.

It's more of an annoyance than anything, but I'd like to know why it's happening, and of course how to fix it and improve my boot times.

I'm using Intrepid 8.10.

Many thanks in advance
Paul

---

### Post by potatan on 2009-02-20
Friday afternoon bump :)

---

### Post by pwerner2 on 2009-02-23
Press escape to enter the grub menu immediately during boot. Highlight the kernel version that you intend to use and press "e". Add "noresume" to the end of this line, exit, then press "b" to boot.

---

