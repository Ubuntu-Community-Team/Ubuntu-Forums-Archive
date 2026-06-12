---
title: "problems with Breezy, Wacom Graphire3, GIMP"
date: 2005-12-26
forum: Desktop Environments
---

### Post by edheil on 2005-12-26
Hullo.

I wanted to get my wacom tablet working, so I installed these modules:

wacom-tools - utilities for wacom tablets and other hid devices
xserver-xorg-input-wacom - X.Org X server -- Wacom input driver
wacom-kernel-source - source for the wacom binary modules

made these changes to xorg.conf: (note that I never use the tablet mouse so I left out "cursor")

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option                "SendCoreEvents"        "true"
  Option        "Device"        "/dev/input/wacom"   # USB ONLY
  Option        "Type"          "stylus"
  Option        "USB"           "on"                  # USB ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
        Option          "SendCoreEvents"        "true"
  Option        "Device"        "/dev/input/wacom"   # USB ONLY
  Option        "Type"          "eraser"
  Option        "USB"           "on"                  # USB ONLY
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "Synaptics Touchpad"
   InputDevice "stylus"
   InputDevice "eraser"
EndSection

and rebooted, with the wacom plugged in.

In the GIMP, I configured 'stylus' and 'eraser' to use screen mode.

I can now get pressure support in the GIMP, but it has a weird and fatal side effect.  When I use a pressure sensitive tool, I lose the ability to do anything with the mouse pointer but paint with that tool.   ANYTHING.  I can't click on menu items, focus windows, make selections, ANYTHING.

This remains true if I switch from stylus to eraser or use the touchpad or eraserhead pointing device on my thinkpad.  I still can't click or focus or select anything.

I can't even use the keyboard to affect stuff in X -- no alt tab switching, no keyboard shortcuts.  The only thing I can do (and thankfully, at least it works) is control-alt-backspace to kill X.  Often X does not restart by hand and I have to issue a restart to /etc/init.d/gdm to get it back.

I'm really happy to see the pressure sensitivity working but obviously this won't do.  any debugging/fixing hints?

Thanks!

Ed

---

### Post by 23meg on 2005-12-26
Did you try the "Window" mode as well? How about setting "cursor" to "Screen" mode?

---

### Post by edheil on 2005-12-26
I just tried the Window mode, and found that it has the same drawback: the GIMP seems not to want to "give the cursor back."  In this case I was able to get out of it using keyboard shortcuts; I'm almost positive it had reached the point before where it wouldn't even let me do that, but maybe I'm misremembering.  I've tried a lot of things. 

I just added a "cursor" section to xfree and set cursor to "screen" in the GIMP; that doesn't seem to change anything.

Any other ideas?  I really appreciate the quick reply!

UPDATING: it seems to be the case that when this happens, alt-tab doesn't work, so one can't get to another window; clicking on other things to focus a different window/panel/menu/whatever doesn't work; however, keyboard shortcuts *within the focused gimp window* work so one can do a "file/close" and get out of the GIMP, avoiding the need to bail out of X11 completely.

I guess this is kind of a GIMP problem -- the gimp grabbing the pointer and not letting go come hell or high water....

---

### Post by edheil on 2005-12-26
WOO!  I think I've got it.  I had not changed 

        Option          "Device"                "/dev/input/mice"

to:

        Option          "Device"                "/dev/input/mouse0"

changing that took care of it. :)  (it also disabled my pencil-eraser pointing device but I never used that anyway)

---

