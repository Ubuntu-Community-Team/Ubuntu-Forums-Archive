---
title: "Amarok woes"
date: 2008-04-06
forum: Desktop Environments
---

### Post by harrybazeegar on 2008-04-06
Hi all...

I am using ubuntu... 
i wanted to try out amarok... so i installed it.

I also thought amarok might need kde stuff so i installed kde too ( so now i have that desktop environment separately)

I installed gsteamer0.8-mad for mp3 support.

now amarok starts fine( i run it from GNOME)... but the console output says there are errors.
and when i try to load anything into the playlist amarok just freezes over and the KDE crash notifier comes up( yes, in GNOME).

I have attacked the console output here... plz tell me what these errors mean, and what I need to do to get amarok run :)

```

X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kbuildsycoca running...
Reusing existing ksycoca
kio (KService*): WARNING: The desktop entry file /usr/share/applications/DefaultPlugins.desktop has Type=Link instead of "Application" or "Service"
kio (KService*): WARNING: Invalid Service : /usr/share/applications/DefaultPlugins.desktop
kio (KSycoca): ERROR: No database available!
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x8094ad8 ): KAccel object already contains an action name "play_pause"
QLayout "unnamed" added to QVBox "unnamed", which already has a layout
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x8094ad8 ): KAccel object already contains an action name "play_pause"
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
QObject::connect: Incompatible sender/receiver arguments
        StarManager::ratingsColorsChanged() --> ContextBrowser::ratingOrScoreOrLabelsChanged(const QString&)
harshath@bazeegar:~$ kio (KIOConnection): ERROR: Header read failed, errno=104
kio (KIOConnection): ERROR: Header has invalid size (-1)
kio (KIOConnection): ERROR: Header read failed, errno=104
kio (KIOConnection): ERROR: Header has invalid size (-1)
kio (KLauncher): ERROR: SlavePool: No communication with slave.
Very strange! got a DCOPReplyWait opcode, but we were not waiting for a reply!
Very strange! got a DCOPReplyDelayed opcode, but we were not waiting for a reply!
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
DCOP aborting call from 'anonymous-7353' to 'knotify'
ERROR: Communication problem with knotify, it probably crashed.
KCrash: Application 'knotify' crashing...
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device


```

I almost deserted GNOME and switched to KDE just for amarok, but it wouldn't work in KDE either :(

---

### Post by harrybazeegar on 2008-04-07
/bump

---

### Post by harrybazeegar on 2008-04-12
/bump

---

