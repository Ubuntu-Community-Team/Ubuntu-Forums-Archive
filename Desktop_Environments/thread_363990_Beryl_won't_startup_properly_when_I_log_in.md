---
title: "Beryl won't startup properly when I log in"
date: 2007-02-17
forum: Desktop Environments
---

### Post by CaptSaltyJack on 2007-02-17
(note, i'm using Kubuntu Edgy)

I don't understand what I'm doing wrong here.  I followed the instructions on the Ubuntu wiki and copied the beryl-manager.desktop file into my ~/.kde/Autostart dir.  Sure enough, the Beryl Manager starts up, but the window manager is always set to "KDE" by default.  I have to manually switch it to "Beryl."  Any idea what I'm missing here?  Then I'll probably go modify the wiki because clearly it's missing a step somewhere..

---

### Post by CaptSaltyJack on 2007-02-17
OK, this is odd.  If I just run beryl-manager manually from a Konsole, it works fine.  But in Autostart, it doesn't.

Also, I do get some errors when I run beryl-manager, are these anything I should worry about?

```
myusername@myhost:~$ beryl-manager
myusername@myhost:~$ X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : NVIDIA

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : failed

No GLX_EXT_texture_from_pixmap
beryl: No GLXFBConfig for default depth, falling back on visinfo.
Reloading options
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

```

---

### Post by CaptSaltyJack on 2007-02-18
Nevermind, figured it out by chance.  Making a shell script and putting a "sleep 3" statement before "beryl-manager" did the trick.  I guess X hasn't fully loaded up everything yet, and if the beryl-manager starts too easly, KDE's win manager takes over.

---

