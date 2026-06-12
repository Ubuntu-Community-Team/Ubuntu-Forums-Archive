---
title: "Amarok crashes at second start"
date: 2006-01-28
forum: Desktop Environments
---

### Post by Seebi on 2006-01-28
Hi there, I have a problem with amarok @ ubuntu 5.10:

If i have no config-files in my home, amarok starts correct with the wizard and creates my collection correctly but after quitting and starting again (and every new start) amarok crashes. I have testet the actual packet, the newest packet and i compiled the newest amarok. Everytime the same.

Here is the amarok output:

$ amarok
amaroK: [Loader] Starting amarokapp..
amaroK: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
kbuildsycoca running...
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
KCrash: Application 'amarok' crashing...

Sometimes this output comes;

$ amarok
amaroK: [Loader] Starting amarokapp..
amaroK: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
kbuildsycoca running...
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  7
  Minor opcode:  0
  Resource id:  0x3c00037
KCrash: Application 'amarok' crashing...

Has anybody an idea how i can use amarok?

---

### Post by asimon on 2006-01-28
Breezy has Amarok version 1.3.1, right? The current version is 1.3.8 and they have fixed several crash bugs in the last couple of versions. Is there a more recent amarok version in Breezy Backports? Maybe you should then try that, it could be that it fixes your problem.

---

### Post by cwaldbieser on 2006-01-28
> **Seebi]Hi there, I have a problem with amarok @ ubuntu 5.10:

If i have no config-files in my home, amarok starts correct with the wizard and creates my collection correctly but after quitting and starting again (and every new start) amarok crashes. I have testet the actual packet, the newest packet and i compiled the newest amarok. Everytime the same.

Here is the amarok output:

$ amarok
amaroK: [Loader] Starting amarokapp..
amaroK: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
kbuildsycoca running...
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
KCrash: Application 'amarok' crashing...

Sometimes this output comes said:**
>  Starting amarokapp..
amaroK: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
kbuildsycoca running...
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  7
  Minor opcode:  0
  Resource id:  0x3c00037
KCrash: Application 'amarok' crashing...

Has anybody an idea how i can use amarok?

Well, it seems like something in the config file it creates causes it to crash.  You could try looking at your ".kde/share/config/amarokrc" file and see if there is anything odd about it.  Experiment by removing parts and see if the program will start.

---

### Post by Ulrik on 2006-01-28
Amarok 1.3.7 is in breezy-backports. However, it has issues of its own. Refused to start on my machine after the upgrade due to a permission error.

---

### Post by Seebi on 2006-01-29
[QUOTE=asimon]Is there a more recent amarok version in Breezy Backports? Maybe you should then try that, it could be that it fixes your problem.[/QUOTE]

No. As i write above, I have also tested the newest version (as package and from sources too)

But the app crashes and crashes ...

---

### Post by Seebi on 2006-01-29
[QUOTE=cwaldbieser]Well, it seems like something in the config file it creates causes it to crash.  You could try looking at your ".kde/share/config/amarokrc" file and see if there is anything odd about it.  Experiment by removing parts and see if the program will start.[/QUOTE]

Mhmm, it seems this is not a amarok specific problem. i tested juk and this app crashes too. Maybe a problem with gstreamer? But Rythmbox works fine.

Is there something i have to attend if i want to use KDE apps with gnome?

Thx

S.

---

