---
title: "[SOLVED] unable to connect to repositories for updates 1420n"
date: 2008-07-11
forum: Dell Ubuntu Support (CLOSED)
---

### Post by trooperchix on 2008-07-11
Since this last update (last updated the night before last), I have been unable to download any updates as evidently the system cannot connect with the ubuntu hardy repositories.  Is anyone else having this problem and does anyone have an answer?  It was running smooth as all get out until the night before last...

Thanks:confused:

---

### Post by ajgreeny on 2008-07-11
if you use synaptic, does it show any broken packages in the system bar at the bottom?  The only updates on 9th July were various *bind* packages all to do with dns servers and the internet so I wonder if one of them did not install properly.  Also do you have libdns35 installed? This was an additional package on the 9th, not an upgrade.  Perhaps you need to download and install that manually if you do not have it.

---

### Post by trooperchix on 2008-07-11
I have libdns35 installed, and the system bar on the bottom of synaptic manager states all is good.  Any other ideas?

---

### Post by trooperchix on 2008-07-11
wow, for some reason it just let me update, but it was painfully slow.  BTW, is there something like a disk defrag on hardy?

---

### Post by ajgreeny on 2008-07-11
No defrag needed in ext3 file systems.

---

