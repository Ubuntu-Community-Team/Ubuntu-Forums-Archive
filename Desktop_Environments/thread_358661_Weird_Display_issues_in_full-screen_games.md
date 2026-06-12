---
title: "Weird Display issues in full-screen games"
date: 2007-02-11
forum: Desktop Environments
---

### Post by hartz on 2007-02-11
I'm not much of a gamer (I suck at most games) but I chanced upon a few gaming threads a few days ago, and some people were raving about their favorite games (Threads along the lines of There are no good games under Linux/yes there are)

So curiosity bit me and I tried to install a few from the package databases.  (Actually I selected just about every single game I could find and its data files, and then let the computer download some 900 MBs or so overnight)

The strange behavior appears when switching eg Frozen Buble or Emilia Pinball to full screen mode.  The same weird behavior appears in other games which I assume are full-screen only games, eg Tremulous.

For reference: 
[LIST]
[*]I have X set up in a dual-screen "TwinView" configuration
[*]The primary display is on the right.
[*]I am using the Nvidia drivers (1.0-9746) built from the Nvidia install script.  
[*]I have Beryl working but disabled during this testing, I use it only occasionally when impressing friends/family <grin>
[/LIST]

Two things happen when I run a full-screen game under X:
Firstly, the game is initially displayed over the right edge of the primary monitor.  Only 50% of the game is visible.  Pushing the mouse to the right brings the game into view.  I can make a little video clip of this if I am not clear, but for now I attach a photo.  I will try to list the effects here concisely:

1) The secondary (left) monitor goes into power-save mode.
2) The primary Monitor switch mode (makes static clicking sound like when switching resolution and/or refresh rates)
3) The game appears centered on the right edge of the right (primary) monitor.  In other words, only the left half of the game is visible.
4) The right-third (maybe?) of left-monitor of the X desktop display appears on the left half of the primary (right) monitor as a vertical strip.
5) No mouse pointer is visible
6) Pushing the mouse to the right brings the right half of the game into view, and partially pushes the remaining X desktop display out the left side of the monitor.
7) The game is not maximized, but appears to fill a square approximately 800x640.  This varies depending on the game's supported resolutions.
8 ) It seems that the monitor is still in 1600x1200 mode as the visible X-desktop portion is filling the screen from top-to-bottom and looks like it is in correct aspect ratio.
9) Pushing the mouse to the right brings the game into view only just.  At maximum, the right edge of the game is on the right edge of the monitor, and the left edge in the center of the monitor (for an 800x640 game).  Pushing the mouse to the left has no effect, the game does not move back out of the display.  There is no upward/downward movement.

A Note on games like Tux Racer and Globulation which supports full-screen 3200x1200 mode: in these games the display perfectly fills both monitors (only when enabling 3200x1200 mode), in which case none of the above are true.  Also with these same games, when selecting 1600x1200 mode, the game centers on the center of the right monitor, and then obviously fills the entire monitor, and no parts of the X display remains, it works perfectly - The problem appears to be only with games that does not use the full resolution of my monitors.

I would like these lower-resolution games to fill up the entire monitor, and at the very least, display in the middle of one of the two monitors.

Any advice?

The second type of weirdness that I experience with seemingly all full-screen games is that sometimes they think they are in full-screen mode, but they are actually in windowed mode.  Restarting the game sometimes fixes the mode (without changing any settings).  Repeatedly starting and quiting any one of these games randomly enters either full-screen or windowed mode, there appears to be no way to determine whether the game will successfully enter full-screen mode or not.  Where the game actually have settings in-game to change between full-screen and windowed mode (eg Tux racer), toggling the mode to windowed and then back to full-screen fixes this too.  This is not a huge problem, but a little perturbing.

Thirdly, In Nexius I notice that whenever I make the display settings wider than 1600x???, the in-game mouse starts to work.  At 1600x??? or less, I get an X-Windows mouse pointer overlaying the game, which makes the game unplayable.  When setting the video width to greater than 1600x??? I get the display centered across both screens, which doesn't work as the monitors' cover is too much of an interruption to my sense of reality to be able to run around in a split-world with a 2-inch wide gap!  The game seems to be broken though, I keep accidentally running out of the graphics (world) through the walls, and then see a broken view.

I notice that the update manager have just installed many updates for libgnome, GTK and Beryl and various other libraries (some 65 MB) and requested a reboot.  I will work in a reboot later today to see if anything changes/improves, though just having installed the updates has made no difference.

The promised picture of the weird display (936KB, 2270x1704) : [http://hartz.co.za/photos/new/weird_display.jpg](http://hartz.co.za/photos/new/weird_display.jpg)

---

### Post by hartz on 2007-02-11
bump

---

### Post by hartz on 2007-02-12
last bump.

---

### Post by GoingDown on 2007-02-12
No solution, but when I am using dual monitors, my games are doing the same. I am using ATI, so I thing it is an X issue. Only way to get it working seems to be to disable 2nd monitor when gaming

---

### Post by hartz on 2007-02-12
Well, for the record, the recent updates and subsequent reboot made no difference.

---

### Post by barakaspeed on 2008-05-05
I'm having the same exact issue with my dual monitors on nvidia.  I also noticed another issue, possibly related.  When I press "Ctrl + Alt + +" or "Ctrl + Alt + -" to switch to different resolutions, my second monitor goes into standy (as desired) but then my other monitor displays performs spanning for both desktops.  Panning is not enabled in my xorg.conf to my knowledge.  I can post it when I get home from work.  Anyone have this issue as well to see if it's related to this gaming issue?

EDIT:

Here is a thread that states my point.  I do feel these two issues are related.
[http://ubuntuforums.org/showthread.php?t=653491](http://ubuntuforums.org/showthread.php?t=653491)

Here's my xorg.conf

```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildd@vernadsky)  Tue Mar  4 20:24:34 UTC 2008

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    InputDevice    "Synaptics Touchpad"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
EndSection

Section "InputDevice"
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "HorizEdgeScroll" "0"
    Option         "SHMConfig" "on"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "WDE L2410NM"
    HorizSync       30.0 - 80.0
    VertRefresh     56.0 - 75.0
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    Option         "NoLogo" "True"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce Go 6800"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
EndSection

Section "Screen"

# Removed Option "metamodes" "CRT: 1920x1200, DFP-1: 1920x1200; CRT: NULL, DFP-1: 1680x1050; CRT: NULL, DFP-1: 1440x900; CRT: NULL, DFP-1: 1280x768; CRT: NULL, DFP-1: 800x600"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
#    Option         "TwinViewOrientation" "RightOf"
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "DFP-1"
    Option         "metamodes" "CRT: 1920x1200 +0+0, DFP-1: 1920x1200 +1920+0; CRT: NULL, DFP-1: 1920x1200 +0+0; CRT: NULL, DFP-1: 1680x1050 +0+0; CRT: NULL, DFP-1: 1600x1024 +0+0; CRT: NULL, DFP-1: 1440x900 +0+0; CRT: NULL, DFP-1: 1400x1050 +0+0; CRT: NULL, DFP-1: 1280x1024 +0+0; CRT: NULL, DFP-1: 1280x960 +0+0; CRT: NULL, DFP-1: 1280x800 +0+0; CRT: NULL, DFP-1: 1280x720 +0+0; CRT: NULL, DFP-1: 1152x864 +0+0; CRT: NULL, DFP-1: 1024x768 +0+0; CRT: NULL, DFP-1: 960x600 +0+0; CRT: NULL, DFP-1: 832x624 +0+0; CRT: NULL, DFP-1: 800x600 +0+0; CRT: NULL, DFP-1: 800x512 +0+0; CRT: NULL, DFP-1: 720x480 +0+0; CRT: NULL, DFP-1: 720x450 +0+0; CRT: NULL, DFP-1: 640x512 +0+0; CRT: NULL, DFP-1: 640x480 +0+0; CRT: NULL, DFP-1: 640x400 +0+0; CRT: NULL, DFP-1: 640x384 +0+0; CRT: NULL, DFP-1: 576x432 +0+0; CRT: NULL, DFP-1: 512x384 +0+0; CRT: NULL, DFP-1: 416x312 +0+0; CRT: NULL, DFP-1: 400x300 +0+0; CRT: NULL, DFP-1: 320x240 +0+0"
EndSection

```

---

