---
title: "Using kate from terminal reports errors"
date: 2007-06-19
forum: Desktop Environments
---

### Post by clk99 on 2007-06-19
Whenever I use kate to open a text file from the terminal I get errors like this:```
$ sudo kate /etc/fstab
Password:
X Error: BadDevice, invalid or uninitialized input device 157
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 157
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
```I guess it isn't a huge problem because it always works anyways, I was just wondering what the errors were.

---

### Post by AdamG51172 on 2007-06-19
I had a similar problem.  It was my experience that I had a bad device in xorg.config.  I had a USB mouse (Clear MacPro) that was plugged in when xorg was configured, but I unplugged it later.  My input device kept showing up as wacom (the graphics tablet) which is either the generic driver it found, or didn't detect my device properly. Anyway, I just commented them out and all was well.  I don't know the specific device errors, but you may find them in one of the threads here.

---

### Post by bailout on 2007-06-19
These usually come from the tablet entries in xorg and can be ignored. 

If launching a graphical command like kate I think you should use kdesu instead of sudo.

---

### Post by Nythain on 2007-06-19
kdesu kate /etc/X11/xorg.conf

comment out the input device entries for the tablet pc like this
```

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
#    InputDevice    "stylus" "SendCoreEvents"
#    InputDevice    "cursor" "SendCoreEvents"
#    InputDevice    "eraser" "SendCoreEvents"
EndSection

```
futher down in that file a chunk that looks like this
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
save the file
control+alt+backspace to reload x and you should never have that problem again

---

### Post by clk99 on 2007-06-20
great, thanks!

---

