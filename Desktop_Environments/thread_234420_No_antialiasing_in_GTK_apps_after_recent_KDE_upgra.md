---
title: "No antialiasing in GTK apps after recent KDE upgrade - solution"
date: 2006-08-11
forum: Desktop Environments
---

### Post by Case_f on 2006-08-11
I thought it could come in handy for some users if I post this. Maybe it was mentioned before, but I couldn't find it here.

 After the upgrade to KDE 3.5.4 (from 'latest' Kubuntu repository), I've lost antialiased fonts in GTK applications for no apparent reason, and nothing I thought of seemed to work. But today I've finally found the solution - it seems to be some kind of bug in KDE and there's an easy workaround: Go to Font settings and change the General font to any font other than the one you had set before. Voila, GTK apps appear fine. You may now set the General font back to your favourite one, the problem is gone.

---

### Post by Sebastian Stein on 2006-08-15
Thanks, that fix really worked. The problem with anti-aliased fonts in KDE is repeating since several years now. It is really a shame.


Sebastian

---

### Post by treris on 2006-08-18
Worked like a freakin charm, thanks a bunch!!!! It was annoying the living daylights out of me everything I started up Synaptic or Firestarter. Yeah I know those aren't kde programs but I just like 'em better than Adept or a kde firewall (if there is such a thing)

---

### Post by TD-Linux on 2006-08-20
Hmm... even Konqueror is antialiased - the only thing that is antialiased is the KDE bar and the associated menus, along with the Control Center.
I have to restart my KDE session for this to take effect, right?

---

### Post by Case_f on 2006-08-21
If I remember correctly, there was no need for enfing the session and starting new one, it worked 'on-the-fly'. But this 'fix' only affects antialiasing in GTK apps under KDE (i.e. Synaptic, as mentioned before). If you have problems with antialiasing in KDE, it's probably something else.

---

