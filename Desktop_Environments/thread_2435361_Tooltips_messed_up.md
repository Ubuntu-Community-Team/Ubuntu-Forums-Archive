---
title: "Tooltips messed up"
date: 2020-01-20
forum: Desktop Environments
---

### Post by rabbit83 on 2020-01-20
Hi,

since the last xserver-upgrade the tooltips in my Ubuntu 18.04. are messed up (see Screenshot). It occurs with different themes and user profiles, but only when using X11. With Wayland, the tooltips are displayed correctly. I'm using a ATI/AMD HD 5570 with radeon driver. Any hints?

---

### Post by Pandanus on 2020-01-20
same problem here, but on Ubuntu Budgie 18.04.3.
Furthermore, strangely only some mouseover info-boxes are affected (this is consistent, e.g. tooltip for 'Budgie Desktop Settings' is never affected, and the one for 'Budgie Complete Installation' is always garbled. This is also not restricted to the desktop environment, but happens in programs (firefox, gimp) and on the plank dock. 
Also using a Radeon (Radeon HD 5470) with radeon driver.

[IMG]https://abload.de/img/text_distortedeqk4o.png[/IMG]

---

### Post by guiverc on 2020-01-20
I've seen the same on Ask Ubuntu; recall it having experienced similar on a Kubuntu qa-test (19.10; lp.[1845823]("https://bugs.launchpad.net/ubuntu/+source/systemsettings/+bug/1845823")).  If you file or find a bug a bug, please note it here for me please). Thanks

---

### Post by rabbit83 on 2020-01-21
@guiverc: Have you tried the new packages from [https://bugs.launchpad.net/ubuntu/eoan/+source/mesa/+bug/1841718]("https://bugs.launchpad.net/ubuntu/eoan/+source/mesa/+bug/1841718")? They fixed the bug for me (regular update will follow soon).

---

### Post by dora5 on 2020-02-02
This was a bug in X.org and X.org radeon drivers.  The fixes are in the current system updates, just run them.

I ran update and upgrade, and tooltips no longer tear.  Sometimes they don't display at all, but they are no longer driving me buggy.

---

