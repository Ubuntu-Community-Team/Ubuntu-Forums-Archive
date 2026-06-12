---
title: "gdesklets not working, and cooking my CPU"
date: 2005-04-23
forum: Desktop Environments
---

### Post by Rehevkor on 2005-04-23
I installed gdesklets via Synaptic and started the daemon, and my CPU usage immediately hit 100% and stayed there. I was able to open the desklet manager, but I couldn't get any of them to display. I had to reboot to get rid of the CPU usage problem.

Anyone have a clue what's going on here?

---

### Post by Nis on 2005-04-24
If you installed gdesklets-data be advised that many of the desklets in that package no longer work with gDesklets 0.34.  Try posting your ~/.gdesklets/gdesklet.0.log (or similar name) here.

---

### Post by Rehevkor on 2005-04-24
Here it is:
```
Log messages of /home/jcestep/.gdesklets/gdesklets:0.0.log

==========================================================[04/23/05-22:40:31]===
Deprecation: Sensors are deprecated since v0.30.
Please consider using controls and inline scripts.



==========================================================[04/23/05-22:40:31]===
Deprecation: Sensors are deprecated since v0.30.
Please consider using controls and inline scripts.



==========================================================[04/23/05-22:40:31]===
Deprecation: Sensors are deprecated since v0.30.
Please consider using controls and inline scripts.



==========================================================[04/23/05-22:40:31]===
Deprecation: Sensors are deprecated since v0.30.
Please consider using controls and inline scripts.



==========================================================[04/23/05-22:40:31]===
Adding "/usr/share/gdesklets/Displays/ltenhallmail/LTenhallmail.display" with ID "id11143093439439970" to the desklet list.



==========================================================[04/23/05-22:40:32]===
Deprecation: Sensors are deprecated since v0.30.
Please consider using controls and inline scripts.



==========================================================[04/23/05-22:40:32]===
Deprecation: Sensors are deprecated since v0.30.
Please consider using controls and inline scripts.



==========================================================[04/23/05-22:40:32]===
Deprecation: Sensors are deprecated since v0.30.
Please consider using controls and inline scripts.



==========================================================[04/23/05-22:40:32]===
Deprecation: Sensors are deprecated since v0.30.
Please consider using controls and inline scripts.



==========================================================[04/23/05-22:40:32]===
Adding "/usr/share/gdesklets/Displays/ltenhallmail/LTenhallmail.display" with ID "id1114309361446392" to the desklet list.

```

---

### Post by Motomouse on 2005-04-24
you also might take a look at

[http://adesklets.sourceforge.net/](http://adesklets.sourceforge.net/)

ragards 
ralph

---

