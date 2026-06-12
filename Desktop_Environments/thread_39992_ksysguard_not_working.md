---
title: "ksysguard not working"
date: 2005-06-07
forum: Desktop Environments
---

### Post by blakken on 2005-06-07
actually since the very beginning of my kubuntu installation I realized that ksysguard doesn't want to show me any process;when clicking over it it asks connect to host ssh protocole and do on ,I'm actually lost ,whateverr protocol i'm trying none of them is working,anybody made it work properly?thanx!

---

### Post by PantherFarber on 2005-07-06
i also have the same problem. i have found out that it doesnt connect to ksysguardd because it isnt running. when i try to run ksysguardd this is the result:

dan@mobiletux:~$ sudo ksysguardd
Password:
ksysguardd 1.2.0
(c) 1999, 2000, 2001, 2002 Chris Schlaeger <cs@kde.org> and
(c) 2001 Tobias Koenig <tokoe@kde.org>
This program is part of the KDE Project and licensed under
the GNU GPL version 2. See [http://www.kde.org](http://www.kde.org) for details.
Segmentation fault
dan@mobiletux:~$

i have tried removing and reinstalling ksysguard with no effect. always the same results. it was working after i installed kubuntu but then stopped.

---

