---
title: "amaroK crashing on startup"
date: 2005-12-18
forum: Desktop Environments
---

### Post by Vulpus on 2005-12-18
I have been using amaroK 1.3 on Breezy for ages without problem but now it has suddenly started chrashing on startup.  It almost finishes loading but when the the progress bar at the bottom gets to 32% it crashes.  If I run it from terminal I get the following:

dt@viglen:~$ amarok
amaroK: [Loader] Starting amarokapp..
amaroK: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokap p.
DCOPClient::attachInternal. Attach failed Could not open network socket
kbuildsycoca running...
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for Play listWindow/PlaylistWindow
QPainter::begin: Cannot paint null pixmap
dt@viglen:~$ kio (Scheduler): FATAL: BUG! _ScheduleJob(): No extraJobData for jo b!
kio (KIOConnection): ERROR: Header read failed, errno=104
kio (KIOConnection): ERROR: Header has invalid size (-1)
kio (KIOConnection): ERROR: Header read failed, errno=104
kio (KIOConnection): ERROR: Header has invalid size (-1)
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  7
  Minor opcode:  0
  Resource id:  0x3000037
QWidget::setMaximumSize: (unnamed/RecipientComboBox) The largest allowed size is  (32767,32767)
dt@viglen:~$

Any advive gratefully appreciated.  I cannot live without amaroK!

---

### Post by Vulpus on 2005-12-20
Surely there must be SOMEBODY out there who can give me a clue at least.  I have tried uninstalling and then re-installing amaroK.  I have tried all the tips I could find on google (but they all relate to KDE) and i have tried re-tagging all my 11,000 MP3s.  STILL amaroK crashes on start up.  It used to be my most used application, now it is just taking up valuable disk space.

---

### Post by pedrorolo on 2006-01-08
[QUOTE=Vulpus]I have been using amaroK 1.3 on Breezy for ages without problem but now it has suddenly started chrashing on startup.  It almost finishes loading but when the the progress bar at the bottom gets to 32% it crashes.  If I run it from terminal I get the following:

dt@viglen:~$ amarok
amaroK: [Loader] Starting amarokapp..
amaroK: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokap p.
DCOPClient::attachInternal. Attach failed Could not open network socket
kbuildsycoca running...
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for Play listWindow/PlaylistWindow
QPainter::begin: Cannot paint null pixmap
dt@viglen:~$ kio (Scheduler): FATAL: BUG! _ScheduleJob(): No extraJobData for jo b!
kio (KIOConnection): ERROR: Header read failed, errno=104
kio (KIOConnection): ERROR: Header has invalid size (-1)
kio (KIOConnection): ERROR: Header read failed, errno=104
kio (KIOConnection): ERROR: Header has invalid size (-1)
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  7
  Minor opcode:  0
  Resource id:  0x3000037
QWidget::setMaximumSize: (unnamed/RecipientComboBox) The largest allowed size is  (32767,32767)
dt@viglen:~$

Any advive gratefully appreciated.  I cannot live without amaroK![/QUOTE]

maybe this and your problem are the same:
[http://ubuntuforums.org/showthread.php?t=95755&highlight=amarok+kio](http://ubuntuforums.org/showthread.php?t=95755&highlight=amarok+kio)

you should search the foruns before posting.

---

