---
title: "Mouse goes berzerk"
date: 2006-08-09
forum: Desktop Environments
---

### Post by edantes on 2006-08-09
I just switched from Fedora 5 to Ubuntu 6.06 (2.6.15-26-386), running on a Dell Inspiron 8100.  Like it so far, problems with my CD-ROM reader and Wifi went away.  However ...

Every once in a while my mouse goes crazy.  Pointer disappears, windows start to pop-up or scroll wildly.  A couple of seconds later the hurricane stops and everything is back to normal except for the messed-up desktop.  This is an external optical PS/2 mouse that disables the built-in synaptic touchpad.

Any ideas of what to do to get a better diagnostic of this problem?

The hardware works with FC5 and XP.

Merci d'avance

---

### Post by rekahsoft on 2006-08-09
Try a different mouse...that will show weather it is a hardware problem or a software problem...then report back.

---

### Post by edantes on 2006-08-09
It doesn't happen with the touchpad. Of course, it doesn't prove anything: different driver, different hardware interface.

After googling a bit, I found similar reports on ubuntu and other Debian distros.  It is hard to trace, it might be a driver bug or a hardware problem.  I will try another mouse later today.

The event is a loss of mouse synchronization.  Here is a typical excerpt from /var/log/messages:

Aug  9 16:30:55 ggv-ubuntu kernel: [17192534.288000] psmouse.c: Wheel Mouse at isa0060/serio1/input0 lost synchronization, throwing 2 bytes away.
Aug  9 16:30:56 ggv-ubuntu kernel: [17192534.920000] psmouse.c: Wheel Mouse at isa0060/serio1/input0 lost synchronization, throwing 2 bytes away.
Aug  9 16:32:34 ggv-ubuntu kernel: [17192633.416000] psmouse.c: Wheel Mouse at isa0060/serio1/input0 lost synchronization, throwing 3 bytes away.
Aug  9 16:32:42 ggv-ubuntu kernel: [17192641.444000] psmouse.c: Wheel Mouse at isa0060/serio1/input0 lost synchronization, throwing 1 bytes away.

---

### Post by edantes on 2006-08-09
An update:

It looks like a pcmouse driver bug.  It happens with a PS/2 logitech I tried, but not as severely or often.

---

