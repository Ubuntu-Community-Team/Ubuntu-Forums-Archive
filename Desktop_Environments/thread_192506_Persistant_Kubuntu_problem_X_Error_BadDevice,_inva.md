---
title: "Persistant Kubuntu problem: X Error: BadDevice, invalid or uninitialized input device"
date: 2006-06-08
forum: Desktop Environments
---

### Post by Hikaru79 on 2006-06-08
I installed kubuntu-desktop on top of  a regular Ubuntu install. Everything seems to work great, but whenever I run just about any program from the CLI, it gives:
```
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
``` 
The program still seems to function fully, but its still a little bit worrying when I get that all the time. Even when adding new packages to Synaptic, the terminal screen in the GUI is filled with that error.

Anyone know what gives? Thanks in advance :)

---

### Post by Skye on 2006-06-08
I've seen that as well on my (regular) Ubuntu box, so I don't think it's specific to the Kubuntu flavor.

---

### Post by Hikaru79 on 2006-06-08
Ah, I've solved my own problem! Go into xorg.conf and comment out the following lines:
```
#    InputDevice    "stylus" "SendCoreEvents"
#    InputDevice    "cursor" "SendCoreEvents"
#    InputDevice    "eraser" "SendCoreEvents"
```
And:
```
#Section "InputDevice"
#
#                                                      # /dev/input/event
#                                                      # for USB
#    Identifier     "stylus"
#    Driver         "wacom"
#    Option         "Device" "/dev/wacom"          # Change to 
#    Option         "Type" "stylus"
#    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
#EndSection
#
#Section "InputDevice"
#
#                                                      # /dev/input/event
#                                                      # for USB
#    Identifier     "eraser"
#    Driver         "wacom"
#    Option         "Device" "/dev/wacom"          # Change to 
#    Option         "Type" "eraser"
#    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
#EndSection
#
#Section "InputDevice"
#
#                                                      # /dev/input/event
#                                                      # for USB
#    Identifier     "cursor"
#    Driver         "wacom"
#    Option         "Device" "/dev/wacom"          # Change to 
#    Option         "Type" "cursor"
#    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
#EndSection
```

Voila! No more problem :) For those of us without wacom tablets, the extra input devices were getting in the way. Hope this helps everyone!

---

### Post by Skye on 2006-06-08
That does it alright.  I don't (nor do I plan to) have any tablet thingimajigs, so I just deleted those sections.  Thanks for the fix, Hikaru79!

---

### Post by cesera on 2006-09-06
> **Hikaru79 said:**
> Ah, I've solved my own problem! Go into xorg.conf and comment out the following lines:
```
#    InputDevice    "stylus" "SendCoreEvents"
#    InputDevice    "cursor" "SendCoreEvents"
#    InputDevice    "eraser" "SendCoreEvents"
```

 
Thank you very much for this, I had been wondering what was causing this. This forum is a great source of information.

---

### Post by karloz on 2007-02-05
Thank you for that solution.  I installed Kubuntu yesterday and these error messages have been driving me nuts!

---

