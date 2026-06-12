---
title: "Orange &quot;Updates Available&quot; top tray icon gone in 9.04, was in 8.04"
date: 2009-09-15
forum: Desktop Environments
---

### Post by mdlueck on 2009-09-15
I recently loaded up a new system, and installed 9.04. On my previous system I had been running 8.04.

8.04, like 7.04, had an orange top tray icon which would appear when updates were available. When that would appear, I would launch Synaptic and apply the updates.

In 9.04, I see an "Update Manager" window appear at times in the bottom of the screen, have to click it after it gets done checking... I run like 15 workspaces and the "Update Manager" does not seem to travel well between workspaces, etc...

So, what / how can one reconfigure back the familiar orange top tray icon and get rid of the annoying "Update Manager" window?

TIA!
Michael

---

### Post by mcduck on 2009-09-16
Open Gconf-Editor (alt-F2 and run "gconf-editor"), browse to apps/update-notifier and disable the "auto_launch"-key. That will give you back the old behavior. :)

---

### Post by mdlueck on 2009-09-18
Greetings mcduck:

Well waddajaknow!!! I just received a top tray icon - Red arrow with a ! inside. "Updates Available"

This solution works like a charm.

Thanks very much, mcduck!
Michael

P.S. Tere Finland... just noticed your location! ;-)

---

