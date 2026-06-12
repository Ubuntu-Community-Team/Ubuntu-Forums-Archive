---
title: "KDE Autostart: Some applications fail to start"
date: 2009-01-12
forum: Desktop Environments
---

### Post by jacksjj on 2009-01-12
Hi,

I'm using KDE version 3.5.7 and I've beening have problems Autostarting applications from autostart folder in a user account. The applications are non-KDE and they use ssh with X forwarding. For each of the applications I place a copy of its .desktop file in the Autostart folder.

It seems that I consistenly am only able to start 5-6 of the 8 applications that I have in the lauch folder. If I attempt to reduce the number of application in the launch folder to 6, then only 4 applications get started. I've tried changing the [FONT="Courier New"]StartupNotify[/FONT] option in the .desktop file to false but that did not help. If I start the applications via a script, however, with some sleep in between the start calls then the applications will start properly.

Is there anyway to configure the Autostart service to leave more time in between calls to start the applications? Any ideas what might be causing my Autostart woes? 

Thank you.

Jennifer

---

