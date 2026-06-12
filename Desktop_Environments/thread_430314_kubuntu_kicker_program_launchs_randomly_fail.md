---
title: "kubuntu kicker program launchs randomly fail"
date: 2007-05-02
forum: Desktop Environments
---

### Post by destructchaos on 2007-05-02
sometimes, when i launch a program from the kicker, the little icon starts bouncing under my mouse, but the program itself doesn't launch, so i'm stuck watching the icon bounce until the 30 second timeout occurs and i get to try to launch the program again.  i have experienced this on both of my desktops and my lap top.  is this a known bug in KDE?  is there a simple fix?  a complicated one perhaps?

thanks for all your help.

---

### Post by GSF1200S on 2007-05-02
Im having the SAME problem. I thought it was due to ACPI, but after restarting X, Evolution Email immediately wouldnt load, so the screensaver messing things up doesnt stand.

Its a shame, because Im really enjoying the power of KDE, but this is a dealbreaker. And since GNOME freezes left and right, I may end up using XFCE or Fluxbox... This problem is just a deal breaker..

Anybody have ideas?

evolution
CalDAV Eplugin starting up ...
X Error: BadDevice, invalid or uninitialized input device 170
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 170
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Segmentation fault (core dumped)

---

### Post by gpsalt on 2007-05-02
Sorry, IGNORE THIS POST


Refer to older post:
[http://ubuntuforums.org/showthread.php?t=419288&highlight=X+Error%3A+BadDevice%2C]("http://ubuntuforums.org/showthread.php?t=419288&highlight=X+Error%3A+BadDevice%2C")

and solution therein:
[http://kubuntuforums.net/forums/inde...64.0;topicseen]("http://kubuntuforums.net/forums/inde...64.0;topicseen")

---

### Post by GSF1200S on 2007-05-03
Did this work for you? It hasnt for me...

Any other ideas?

---

### Post by destructchaos on 2007-05-13
i made the adjustments to my xorg.conf file about ten minutes ago and have been doing nothing but opening programs since.  not only does it seem to have fixed the problem, but programs appear to be loading faster as well.

if i'm just having a streak of good luck, i'll report it back here.

---

### Post by destructchaos on 2007-05-13
sorry, i spoke too soon.  the posted solution did fix the stuff in the konsole when i launch programs, but it just took me three tries to open Adept, so no solution to the kicker problem yet.

---

