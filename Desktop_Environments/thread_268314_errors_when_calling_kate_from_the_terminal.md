---
title: "errors when calling kate from the terminal"
date: 2006-09-29
forum: Desktop Environments
---

### Post by igknighted on 2006-09-29
When I run kate to edit a file from the terminal, i get the following errors, but the program runs fine... any idea where the errors come from or how I can fix them?  (note, this is in KDE)

$ kate Quadratic.py
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
ScimInputContextPlugin()

---

### Post by pseudonym on 2006-09-30
> **igknighted said:**
> errors when calling kate from the terminal You could try using your phone instead :)

Seriously, though, those errors don't matter. I'm not a regular KDE user, but whenever I have cause to (say, in Knoppix live cd), kate always reacts like that when run from the command line. I'd be lying if I pretended to know exactly what causes those errors, but I've never known them to be a problem which affects things.

---

### Post by Steveire on 2006-10-02
```

kdesu kate /etc/X11/xorg.conf

```
Near the bottom of the file, in the 'ServerLayout' section you'll find lines which you should comment out.
```

#       InputDevice     "stylus" "SendCoreEvents"
#       InputDevice     "cursor" "SendCoreEvents"
#       InputDevice     "eraser" "SendCoreEvents"

```
It works. I don't know why. I suspect only one of them actually needs to be commented out, but I'm happy enough with a working system, so I'm not bothered to check.

---

### Post by hayati on 2006-10-18
yes commenting-out mentioned lines stops error messages. but i wonder if anyone noticed that a KNotify window is trying to appear in menu bar, but it never appears. This means that something wrong is happening, but system is simply ignores errors or cannot process them. I had this problem within a kdevelop qt project(also other gui applications causes same problem when they're called from console). Even after commenting-out mentioned lines KNotify window is about to appear. Cursor changes to wait cursor. But after a couple of seconds everything gets normal. So i thing the solution stops the error messages, but the problem still exists.

---

