---
title: "KDE: display resolution applet missing ?"
date: 2006-07-26
forum: Desktop Environments
---

### Post by matc on 2006-07-26
Hi there,

after a fresh install on one of my computers the system can't find the applet in settings->hardware to change display resolutions.

How can I get it?

---

### Post by asimon on 2006-07-26
Under KDE? Start 'System Settings' and in the 'Hardware' row it's called 'Display'.

If it's not there maybe you don't have the package 'kde-guidance' installed? But it should be installed by default.

---

### Post by matc on 2006-07-26
I'm afraid I know where to find it because I get an error message that the applet is missing.

And kde-guidance is installed:
root@darkbox:~# apt-get install kde-guidance
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut... Fertig
kde-guidance ist schon die neueste Version.
0 aktualisiert, 0 neu installiert, 0 zu entfernen und 0 nicht aktualisiert.

---

### Post by matc on 2006-07-26
Something REALLY strange:
I added in xorg.conf "1600x1200" in screen section, restarted X and suddenly the applet can be found !!!!

In my opinion KDE was independent of X settings, but now it seems to work.

---

