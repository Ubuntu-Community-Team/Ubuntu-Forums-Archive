---
title: "Ubuntu/Windows time conflict"
date: 2006-09-20
forum: Desktop Environments
---

### Post by xster on 2006-09-20
Everytime I get in Ubuntu or Windows, one will have the wrong time and if I change it, the other one would be wrong. For both, the time zone is a mess. Both are set to the right time zone but I think adusting time adjusts different things
How do I change the apparent time in Ubuntu because when I change time zone or time, it changes not the displayed time but the equivalent Greenwich time which makes a mess.

---

### Post by Irony on 2006-09-20
Check your rcS file;

[PHP]gksudo gedit /etc/default/rcS[/PHP]

Change;

[PHP]# Set UTC=yes if your system clock is set to UTC (GMT), and UTC=no if not.
UTC=yes[/PHP]

to;

[PHP]# Set UTC=yes if your system clock is set to UTC (GMT), and UTC=no if not.
UTC=no[/PHP]

---

