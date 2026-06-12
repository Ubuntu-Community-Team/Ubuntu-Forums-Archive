---
title: "What's this error message?"
date: 2006-06-24
forum: Desktop Environments
---

### Post by vigleik on 2006-06-24
Whenever I open a program from the command line (anything, I think) I get the following error message:

$ kcalc&
[1] 5734
$ X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

Everything seems to be working, so this isn't really a problem. Just a tiny little bit annoying, plus it makes me curious what's going on.

By the way, this is happening on two computers. One with the regular 386 kernel and one with the amd64 kernel. In both cases I started by installing ubuntu (because that's what I had) and then "apt-get install kde" to get kde. I haven't checked if this happens in gnome.

Vigleik

---

### Post by Copter on 2006-06-25
same here (Kubuntu 6.06 2.6.15-25-686)

copter :]

---

### Post by siccness on 2006-06-25
I think this is the solution to the problem:
[http://www.ubuntuforums.org/showthread.php?t=185930](http://www.ubuntuforums.org/showthread.php?t=185930)

---

### Post by vigleik on 2006-06-25
[QUOTE=siccness]I think this is the solution to the problem:
[http://www.ubuntuforums.org/showthread.php?t=185930](http://www.ubuntuforums.org/showthread.php?t=185930)[/QUOTE]

Indeed, that made the error message disappear. To summarize what I did to fix it, I made the following changes to my /etc/X11/xorg.conf file: (none of the commented parts were commented out before.)

#Section "InputDevice"
#  Driver        "wacom"
#  Identifier    "stylus"
#  Option        "Device"        "/dev/wacom"          # Change to
#                                                      # /dev/input/event
#                                                      # for USB
#  Option        "Type"          "stylus"
#  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
#EndSection

#Section "InputDevice"
#  Driver        "wacom"
#  Identifier    "eraser"
#  Option        "Device"        "/dev/wacom"          # Change to
#                                                      # /dev/input/event
#                                                      # for USB
#  Option        "Type"          "eraser"
#  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
#EndSection

#Section "InputDevice"
#  Driver        "wacom"
#  Identifier    "cursor"
#  Option        "Device"        "/dev/wacom"          # Change to
#                                                      # /dev/input/event
#                                                      # for USB
#  Option        "Type"          "cursor"
#  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
#EndSection

and this part

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
#       InputDevice     "stylus" "SendCoreEvents"
#       InputDevice     "cursor" "SendCoreEvents"
#       InputDevice     "eraser" "SendCoreEvents"
EndSection

I don't get the error message anymore, but I will post back if this had any bad effects.

Vigleik

---

### Post by Copter on 2006-07-11
thanks, it helped me also ;)

copter :]

---

