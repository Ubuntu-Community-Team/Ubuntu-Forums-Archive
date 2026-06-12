---
title: "Tablet Pen not working"
date: 2008-12-03
forum: General Help
---

### Post by mattimeeleo on 2008-12-03
've been looking through every posts and doing searches on the forums to get my tablet PC to work, but I found no useful solutions. Can you please help me get my Tablet PC's pen/stylus to work?

I have a Tecra M4 running on Ubuntu 8.10

---

### Post by opscure on 2008-12-03
What's inside your /etc/X11/xorg.conf file?  Are you specifying your stylus correctly in there?

I think you should have a
```
InputDevice "stylus" "SendCoreEvents"
```
inside your server layout section and then you should have a InputDevice section that has
```
Section "InputDevice"
Identifier "stylus"
Driver "wacom"
Option "Device" "/dev/input/wacom"
Option "Type" "stylus"
Option "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection
```

If you post your xorg.conf file, I might be able to help you more. I don't have a touch panel that uses a stylus, so I don't know how much help I will be.

---

### Post by opscure on 2008-12-03
You may also want to add a cursor and eraser section to the server layout like above and add your input devices like so:
```
Section "InputDevice"
Identifier "eraser"
Driver "wacom"
Option "Device" "/dev/input/wacom"
Option "Type" "eraser"
Option "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
Identifier "cursor"
Driver "wacom"
Option "Device" "/dev/input/wacom"
Option "Type" "cursor"
Option "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection
```

---

### Post by mattimeeleo on 2008-12-03
Here's my xorg.conf that now works. So the problem is fixed. My friend made the script for me.


```
        # Stylus
Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "stylus"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
        Option         "Button2"       "3"
EndSection

        # Eraser
Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "eraser"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY

        # Fix to auto-switch eraser in Xournal
        Option    "Button1"    "2"
EndSection

        # Cursor
Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "cursor"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
        Option        "Button1"       "2"
EndSection

        # Misc. Stuff
Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "stylus"        "SendCoreEvents"
        InputDevice     "cursor"        "SendCoreEvents"
        InputDevice     "eraser"        "SendCoreEvents"
EndSection
```

---

### Post by opscure on 2008-12-04
Glad to hear it worked out.  Please mark this post as solved.

---

