---
title: "Opera and Kubuntu"
date: 2006-01-05
forum: General Help
---

### Post by eMuNiX on 2006-01-05
I have a small problem, annoyance really, with Opera and Kubuntu.  When I first start the system Opera comes up automatically, which is fine but there is no sound from any sites until I restart Opera.  Anything I can do to quickly fix this?

---

### Post by Pawel Stolowski on 2006-01-05
I don't have opera so I'll be just guessing... This may be caused by arts blocking your soundcard (some cards, e.g. SB Live don't have this problem as they allow concurrent access for multiple applications).

Try one or both of the following:

1. Reduce "auto-suspend if idle after" timeout for arts in System Settings (KControl): ->Sound & Multimedia->Sound System tab.

2. Execute opera with artsdsp wrapper (modify opera menu entry to execute "artsdsp opera")

---

### Post by eMuNiX on 2006-01-06
Seems to have helped Pawel, reducing the auto-suspend if idle from 60 to 10 and it works straight away now.  Couldn't get the second option that you mention to work but that doesn't matter now, thanks for the help :)

---

