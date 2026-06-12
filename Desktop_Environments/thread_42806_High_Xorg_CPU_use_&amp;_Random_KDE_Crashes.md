---
title: "High Xorg CPU use &amp; Random KDE Crashes"
date: 2005-06-19
forum: Desktop Environments
---

### Post by Octane on 2005-06-19
Hey Gang:

First and foremost: I recently switched from FC3 to Kubuntu and couldn't be happier! :grin:  :-P

Specs:
- Mobo: Asus A8V-E Deluxe
- CPU: AMD 64 3200+ Athlon
- RAM: 1GB PC3200 & 1GB Swap
- Video: Nvidia GeForce 6200

ISSUE 1: At what seems to be random times, my Xorg process CPU usage increases to 25-40% and stays there. I have no idea how to trace this. Restarting KDE fixes the problem. Any ideas on what I can do to monitor this more closely and find out what's causing this, will be helpful. I have tried closing all apps, thinking it may be app-related, but that doesn't change anything.

ISSUE 2: I get random X crashes (and I know its X because the Nvidia logo comes up and KDM restarts). I have saved my .xsession-errors logs three times but it doesn't seem like they shed much light. Here are two of them:
```
kate: Fatal IO error: client killed
kaccess: Fatal IO error: client killed
kwin: Fatal IO error: client killed
kicker: Fatal IO error: client killed
klipper: Fatal IO error: client killed
konsole: Fatal IO error: client killed
The application 'gaim' lost its connection to the display :0.0;
most likely the X server was shut down or you killed/destroyed
the application.
xchat: Fatal IO error 104 (Connection reset by peer) on X server :0.0.
kio_uiserver: Fatal IO error: client killed
ksysguard: Fatal IO error: client killed
amarokapp: Fatal IO error: client killed
kded: Fatal IO error: client killed
KWrited - Listening on Device /dev/pts/0
ksmserver: Fatal IO error: client killed
ICE default IO error handler doing an exit(), pid = 15611, errno = 0
ICE default IO error handler doing an exit(), pid = 15626, errno = 0
ICE default IO error handler doing an exit(), pid = 17785, errno = 0
In file kernel/qpixmap_x11.cpp, line 631: Out of memory
KCrash: Application 'konqueror' crashing...
kdeinit: Fatal IO error: client killed
kdeinit: sending SIGHUP to children.
*** KMail got signal 1 (Exiting)
kicker: sighandler called
*** kdesktop got signal 1 (Exiting)
kdesktop: Fatal IO error: client killed
kio (KDirWatch): WARNING: KDirWatch::removeDir can't handle '/'
klauncher: Exiting on signal 1
klauncher: Fatal IO error: client killed
DCOP Cleaning up dead connections.
kdeinit: sending SIGTERM to children.
kicker: sighandler called
DCOP Cleaning up dead connections.
kdeinit: Exit.
```
```
Gecko: Fatal IO error 104 (Connection reset by peer) on X server :0.0.
kicker: Fatal IO error: client killed
klipper: Fatal IO error: client killed
kate: Fatal IO error: client killed
In file kernel/qpixmap_x11.cpp, line 631: Out of memory
KCrash: Application 'konqueror' crashing...
In file kernel/qpixmap_x11.cpp, line 631: Out of memory
KCrash: Application 'konqueror' crashing...
superkaramba: Fatal IO error: client killed
kded: Fatal IO error: client killed
KWrited - Listening on Device /dev/pts/0
kdeinit: Fatal IO error: client killed
kdeinit: sending SIGHUP to children.
kwin: Fatal IO error: client killed
*** kdesktop got signal 1 (Exiting)
*** KMail got signal 1 (Exiting)
klauncher: Exiting on signal 1
klauncher: Fatal IO error: client killed
kdeinit: sending SIGTERM to children.
kdeinit: Exit.
kdeinit: Fatal IO error: client killed
kdeinit: sending SIGHUP to children.
kicker: sighandler called
kicker: sighandler called
QPaintDevice: Cannot destroy paint device that is being painted
```
Thanks for reading and thanks for any help. I know these are tough issues and I know I don't provide too much info 

](*,)

---

### Post by d3s on 2005-06-19
i got that strange issue too and it really gets on my nerves :\ only way to fix is to restart the gui with ctrl+del+backspace comand. hope there is some solution to that problem  :roll: .

---

### Post by Octane on 2005-06-19
[QUOTE=d3s]i got that strange issue too and it really gets on my nerves :\ only way to fix is to restart the gui with ctrl+del+backspace comand. hope there is some solution to that problem  :roll: .[/QUOTE]
Glad to see I'm not the only one :)

---

### Post by d3s on 2005-06-19
i got that strange issue too and it really gets on my nerves :\ only way to fix is to restart the gui with ctrl+del+backspace comand. hope there is some solution to that problem  .

---

### Post by Octane on 2005-06-25
Both these issues were appaerntly related to x.org's Composite (I was using it to have transparency and shadows). I have Disabled it and now both these problems disappeared.

---

