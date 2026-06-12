---
title: "How to get JAVA to work with F1 site"
date: 2009-04-09
forum: General Help
---

### Post by hfxrzw on 2009-04-09
Team, sorry if this has been asked before, but I am to new to this to know what to look for.

I am a big fan of Formula 1 races. After having installed Ubuntu 8.10 on my laptop I tried to use it during the last race to follow the round times etc on the Formula 1 live site, but was unable to. I just got an empty screen, without the applet starting up. The site refers then to a not properly installed or updated JAVA version.
I have now downloaded many different Java packages, but it still does not work. What am I doing wrong?
Appreciate your advise, thanks!! Cheers, Rene.

---

### Post by soltanis on 2009-04-09
There are lots of Javas out there for Linux. If I were you, I'd first uninstall all the ones you've already added. Go to Synaptic (sudo synaptic), search for Java and uninstall any of the Java Runtime Environments you got.

Once that's done, install sun-java6-jre.

When I had problems with java it was because it was using some GNU substitute crap. Using the sun version will provide best performance.

---

### Post by hfxrzw on 2009-04-09
Thanks!! I'll give that a go. Cheers, Rene.

---

### Post by moody_mark on 2009-04-09
Hi, have you installed the ubuntu-restricted-extras?

Go to Applications --> Add / Remove and search for "restricted". Check the "Ubuntu restricted extras" that generally solves a lot of website viewing with java / flash etc

---

