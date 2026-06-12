---
title: "Not working X'es after switching the shadows effect (I can't turn it off)"
date: 2009-02-02
forum: Desktop Environments
---

### Post by darkman30 on 2009-02-02
Hi,
I've installed a KUBUNTU 8.10 with KDE4(+ NVIDIA drivers, actualisations and few programs). Everything was working fine until I opened Desktop Confiuguration and ticked three effects(e.g. shadows), and clicked Apply. Then the window "Confirm settings in 10s." showed and I instant clicked "OK". After this the display turned black. Reseting the system cause entering to log on, and after logging shows the KDE loading bar (this with the icons). Then dsplay turn white and then black (cursor is normally visible). I can see only gray square where I normally have clearweather widget, and where the KDE menu shows, after clicking (from memory), on the place where normally is KDE sign.
I was trying to run Kubuntu in Recovery Mode and choose Try to Configure X Serv (or something like that), but it didn't give anything.
I googled, that it may be drivers fault, so I installed the envy drivers (ofcourse with kdm start and kdm stop), but it didn't change anything.
Essentially, the X'es are working, only the shadows effects etc. makes that I can't see nothing on display. Is there a way to turn them of from the terminal or start the X'es in default configuration?

---

### Post by dabl on 2009-02-02
The crude but effective solution is just to rename the ~/.kde directory to something else, then restart the X server.  This will put you back to a default KDE 4.2 screen, and you'll have to start over with custom configurations.

---

### Post by darkman30 on 2009-02-03
Thank you for your help.

---

