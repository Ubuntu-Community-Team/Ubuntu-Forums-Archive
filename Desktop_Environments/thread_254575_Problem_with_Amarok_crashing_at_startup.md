---
title: "Problem with Amarok crashing at startup"
date: 2006-09-10
forum: Desktop Environments
---

### Post by Bourlotieris on 2006-09-10
I have Amarok version 2:1.3.9-0ubuntu4 installed and it used to work fine for quite some time. But during the past 40 or 50 days I keep on getting the same crash when I start the application (from a terminal):

:~$ amarok
amaroK: [Loader] Starting amarokapp..
amaroK: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
kbuildsycoca running...
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
QPainter::begin: Cannot paint null pixmap
:~$ KCrash: Application 'amarok' crashing...
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  7
  Minor opcode:  0
  Resource id:  0x4600037
amarok: Fatal IO error: client killed
ICE default IO error handler doing an exit(), pid = 1661, errno = 9
Unable to start Dr. Konqi

I am having the same problem in GNOME and KDE. It all started a little while after I installed XGL/Compiz, though I am not sure if it's got anything to do with this. For the past month I have been searching this forum as well as Amarok's but noone seems to have this same problem with me. Any ideas? I am really missing it, now I am stuck with Rhythmbox.

---

