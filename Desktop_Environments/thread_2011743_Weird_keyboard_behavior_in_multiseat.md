---
title: "Weird keyboard behavior in multiseat"
date: 2012-06-27
forum: Desktop Environments
---

### Post by j_kubik on 2012-06-27
I am running Kubuntu 12.04 LTS, and I am currently experimenting with multiseat configuration. Here is my configuration:

xorg.conf
```
Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "kbd_0"                 "CoreKeyboard"
    InputDevice    "mouse_0"               "CorePointer"
    Option         "AutoEnableDevices"     "false"
    Option         "AutoAddDevices"        "false"
    Option         "AllowEmptyInput"       "true"
EndSection
 
Section "ServerLayout"
    Identifier     "Layout1"
    Screen          0  "Screen1" 0 0
    InputDevice    "kbd_1"                 "CoreKeyboard"
    InputDevice    "mouse_1"               "CorePointer"
    Option         "AutoEnableDevices"     "false"
    Option         "AutoAddDevices"        "false"
    Option         "AllowEmptyInput"       "true"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    Identifier     "kbd_0"
    Driver          "evdev"
    Option         "Device"        "/dev/input/jarek-event-kbd"
    Option         "XkbRules"      "xorg"
    Option         "XkbModel"      "105"
    Option         "XkbLayout"     "us"
    Option         "Protocol"      "Standard"
EndSection

Section "InputDevice"
    Identifier     "kbd_1"
    Driver         "evdev"
    Option         "Device"        "/dev/input/liv-event-kbd"
    Option         "XkbRules"      "xorg"
    Option         "XkbModel"      "105"
    Option         "XkbLayout"     "us"
    Option         "Protocol"      "Standard"
EndSection

Section "InputDevice"
    Identifier     "mouse_0"
    Driver         "evdev"
    Option         "Device"        "/dev/input/jarek-event-mouse"
    Option         "GrabDevice"    "on"
EndSection

Section "InputDevice"
    Identifier     "mouse_1"
    Driver         "evdev"
    Option         "Device"        "/dev/input/liv-event-mouse"
    Option         "GrabDevice"    "on"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    Option         "VendorName"    "Unknown"
    Option         "ModelName"     "Generic Autodetecting Monitor"
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    Option         "VendorName"    "Unknown"
    Option         "ModelName"     "Generic Autodetecting Monitor"
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "intel"
    VendorName     ""
    BoardName      ""
    BusID          "PCI:0:2:0"
    Screen         0
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     ""
    BoardName      ""
    BusID          "PCI:1:0:0"
    Screen         0
EndSection

Section "Screen"
        Identifier "Screen0"
        Device     "Device0"
        Monitor    "Monitor0"
        DefaultDepth     24
        SubSection "Display"
                Depth     24
        EndSubSection
EndSection
 
Section "Screen"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

Important parts of kdmrc:

```

[General]
[...]
StaticServers=:0,:1
ReserveServers=:2,:3
ServerVTs=-7,-9
[...]
# Core config for 1st local display
[X-:0-Core]
# The VT the X-server should run on; auto-assign if zero, don't assign if -1.
# Better leave it zero and use ServerVTs.
# Default is 0
#ServerVT=7
# The command line to start the X-server, without display number and VT spec.
# This string is subject to word splitting.
# Default is "/usr/bin/X"
ServerCmd=/root/projects/Xglxmount/Xglxmount /usr/bin/X0 -sharevts -isolateDevice PCI:0:2:0 -layout Layout0
# Enable automatic login. USE WITH EXTREME CARE!
# Default is false
AutoLoginEnable=true
# If true, auto-login after logout. If false, auto-login is performed only
# when a display session starts up.
# Default is false
#AutoLoginAgain=true
# The delay in seconds before automatic login kicks in.
# Default is 0
#AutoLoginDelay=10
# The user to log in automatically. NEVER specify root!
# Default is ""
AutoLoginUser=jarek
# The password for the user to log in automatically. This is NOT required
# unless the user is logged into a NIS or Kerberos domain. If you use this
# option, you should "chmod 600 kdmrc" for obvious reasons.
# Default is ""
#AutoLoginPass=secret!
# Immediately lock the automatically started session. This works only with
# KDE sessions.
# Default is false
#AutoLoginLocked=true
# See above
ClientLogFile=.xsession-errors

# Core config for 1st local display
[X-:1-Core]
# The VT the X-server should run on; auto-assign if zero, don't assign if -1.
# Better leave it zero and use ServerVTs.
# Default is 0
#ServerVT=9
# The command line to start the X-server, without display number and VT spec.
# This string is subject to word splitting.
# Default is "/usr/bin/X"
ServerCmd=/usr/bin/X1 -sharevts -isolateDevice PCI:1:0:0 -layout Layout1
# Enable automatic login. USE WITH EXTREME CARE!
# Default is false
AutoLoginEnable=true
# If true, auto-login after logout. If false, auto-login is performed only
# when a display session starts up.
# Default is false
#AutoLoginAgain=true
# The delay in seconds before automatic login kicks in.
# Default is 0
#AutoLoginDelay=10
# The user to log in automatically. NEVER specify root!
# Default is ""
AutoLoginUser=liv
# The password for the user to log in automatically. This is NOT required
# unless the user is logged into a NIS or Kerberos domain. If you use this
# option, you should "chmod 600 kdmrc" for obvious reasons.
# Default is ""
#AutoLoginPass=secret!
# Immediately lock the automatically started session. This works only with
# KDE sessions.
# Default is false
#AutoLoginLocked=true
# See above
ClientLogFile=.xsession-errors

# Greeter config for 1st local display
[X-:0-Greeter]
# See above
#PreselectUser=Default
# The user to preselect if PreselectUser=Default.
# Default is ""
#DefaultUser=johndoe

# Greeter config for 1st local display
[X-:1-Greeter]
# See above
#PreselectUser=Default
# The user to preselect if PreselectUser=Default.
# Default is ""
#DefaultUser=johndoe

```

Under such configuration my keyboards outputs are working well in X-environment, but every key is also duplicated to virtual terminal going below it. When i switch computer off i see several lines that i recently typed into various windows on the terminal. What's worse, the terminal I am writing to, seems to be the one running startkde command, because every press of Ctrl+C - standard 'copy' combination for many programs kills my session and drops back to login screen. Copying above configs interrupted writing this text twice already ;)... Additionaly it seems that I am unable to switch to virtual terminals - Ctrl+Alt+[1..6] does nothing.

Has anybody an idea how to make X one-and-only owner of keyboard output?

EDIT:

In case anybody wonders about Xglxmount in my xorg.conf - it's small program I wrote myself to make sure that nvidia and mesa OpenGL drivers got loaded for apropriate cards.

EDIT2:

I figured it out - it required Option "GrabDevice" "on" for both keyboards - now it works well. The only problem is not inabilit to use textmode terminals, but If i really ned on, I can still ssh to my machine from another computer...

---

