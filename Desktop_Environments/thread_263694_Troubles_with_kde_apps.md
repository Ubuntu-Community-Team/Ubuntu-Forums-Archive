---
title: "Troubles with kde apps"
date: 2006-09-23
forum: Desktop Environments
---

### Post by msvalverde on 2006-09-23
Since I installed kubuntu-desktop I have lots of troubles with kde apps.
First time I noticed was with k3b. When I try to start it, the graphic environmet gets very slow (mouse jumps) and I have to kill k3b from shell.
I uninstalled kubuntu-desktop, but k3b never worked again. Of course, I tried to reinstall it several times.
Today, I reinstalled kubuntu-desktop again to try k3b into kde, but I just get the same trouble. And that's not all, I get the same troubles with other kde apps, like the image viewer (I can't remember the name).
If I start k3b from a terminal, I get the output:
[FONT="Courier New"]msvalverde@estudio:~$ k3b
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kbuildsycoca running...
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
msvalverde@estudio:~$ ScimInputContextPlugin()
[/FONT]
Any suggestion or may I to reinstall Ubuntu?

---

### Post by ajgreeny on 2006-09-23
Do you get the same errors if you use k3b when in gnome, or only if kde is the desktop running.  It does seem strange as I have a standard ubuntu with kubuntu-desktop installed on top and it all works flawlessly.  Perhaps a hardware conflict of some kind?

The errors are similar to those always present in my .xsession-errors file in my home directory, and I also get them if I start k3b in terminal (I never knew that until I just tried) but k3b still works OK and is not slow at all.  Very strange.

Anybody have any clues?

---

### Post by msvalverde on 2006-09-24
Problems are just the same, both gnome and kde.
Actually, the same using gdm or kdm.

---

