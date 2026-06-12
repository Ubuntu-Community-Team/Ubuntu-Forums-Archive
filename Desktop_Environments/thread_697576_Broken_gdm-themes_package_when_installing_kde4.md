---
title: "Broken gdm-themes package when installing kde4?"
date: 2008-02-15
forum: Desktop Environments
---

### Post by gibbsnich on 2008-02-15
Hi everybody,

since google couldn't help I'm trying here: When I do
[FONT="Courier New"]sudo aptitude install kde4[/FONT]
I get: (sorry for the german..)
[FONT="Courier New"]
Die folgenden Pakete sind KAPUTT: (->broken)
  gdm-themes 
(...)

Die folgenden Pakete haben verletzte Abhängigkeiten:
  gdm-themes: Hängt ab: desktop-base (>= 0.3.15) ist aber nicht installationsfähig
Resolving dependencies...
Die folgenden Aktionen werden diese Abhängigkeiten auflösen:

Beibehalten der folgenden Pakete in ihrer aktuellen Version:
desktop-base [4.0.3 (gutsy, now)]
kdm-kde4 [Nicht installiert]

Die folgenden Abhängigkeiten unaufgelöst beibehalten:
kdebase-workspace empfiehlt kdm-kde4 (>= 4:4.0.1-0ubuntu2~gutsy1~ppa1)
kdebase-kde4 empfiehlt kdm-kde4 (>= 4:4.0.1-0ubuntu2~gutsy1~ppa1)
Bewertungsnote beträgt -270

Diese Lösung akzeptieren? [Y/n/q/?] q[/FONT]

But when I try to install it with synaptic, I got no such message and I was able to install it without any problems..
So: What's aptitude problem?

Thanks!

---

### Post by gibbsnich on 2008-02-15
OK, so synaptic seems to use apt-get which doesn't care about aptitude's flagging. So synaptic shows no "broken package". 
But why does aptitude?

---

