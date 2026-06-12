---
title: "Small White Bar over Menus and Launcher"
date: 2012-03-21
forum: Desktop Environments
---

### Post by grevedan on 2012-03-21
So, anyone seen this issue before, a white bar covering the upper left of the display, its on top of everything?  It shows up eventually after logging in, maybe a few minutes, maybe a few hours.  Logging out will remove the bar, as will restarting the Unity plugin.

Running Unity on Oneiric Ocelot 11.10

[IMG]http://img338.imageshack.us/img338/8177/screenshotat20120321185.png[/IMG]

---

### Post by grevedan on 2012-03-22
No ideas on how to start debugging?

---

### Post by NTolerance on 2012-03-31
I'm getting this on Precise.  Recently it happened as a Chrome desktop notification appeared.  For now ```
unity --replace
``` will make it go away.  We need to find out if a bug has been filed for this.

---

### Post by bagpussnz on 2012-04-01
Hi,
I'm also getting this (12.04 beta2).
Quadro NVS 4200M

A combination of unity --replace and unity --reset got rid of it

Ian

---

### Post by NTolerance on 2012-04-02
Here's the bug report:

[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/940603](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/940603)

---

