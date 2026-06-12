---
title: "CUPS is dead? System&gt;Admin&gt;Printing = dies silently. http://localhost:631 not working"
date: 2005-12-29
forum: Desktop Environments
---

### Post by nbcthreat on 2005-12-29
I'm running Breezy on a Toshiba Tecra with great success. Trying to run Crossover Office has been a generally positive experience, but Word seems to be hanging (it works, but takes about 3 minutes to show up) on CUPS. I tried to go to System>Administration>Printing and the little "Starting Printing" box shows up on the bottom task bar briefly, then dies silently. Later I get a box that says " The CUPS server could not be contacted." [http://localhost:631](http://localhost:631) times out. I've tried reinstalling cupsys and restarting looks like this.

```
david@eris:/etc/cups$ sudo /etc/init.d/cupsys restart
 * Restarting Common Unix Printing System: cupsd                         [ ok ]
david@eris:/etc/cups$

```

Neither action has made any difference. Thoughts?

---

### Post by Bomper on 2006-01-01
1.- sudo gedit /etc/network/interfaces

  2.- And the end of file

        auto lo

---

