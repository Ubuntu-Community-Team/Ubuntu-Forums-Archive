---
title: "Ubuntu 16.04 Scroll wheel emulation not working"
date: 2017-03-08
forum: Desktop Environments
---

### Post by Hakachukai on 2017-03-08
Problem: I'm trying to get my track ball to emulate a scroll wheel when I hold down both Left and Right Mouse buttons and use the track ball.

The 3 button emulation does work ( it emulates button 2 ).

The scroll wheel does not work :-( When I press both buttons it performs a paste action ( if anything has been copied ) instead of activating that scroll wheel


My distro is Ubuntu 16.04 64bit running Gnome classic session 

This is my exact mouse and all of the detail of it:
------------------------------------------------------------------
[https://help.ubuntu.com/community/Logitech_Marblemouse_USB](https://help.ubuntu.com/community/Logitech_Marblemouse_USB)
------------------------------------------------------------------

Contents of my X11 config dir. I have no xorg.conf
------------------------------------------------------------------
user@machine~> ls /usr/share/X11/xorg.conf.d/
total 44K
drwxr-xr-x 2 root root 4.0K Mar  8 19:36 .
drwxr-xr-x 5 root root 4.0K Jul 19  2016 ..
-rw-r--r-- 1 root root   92 Apr  8  2016 10-amdgpu.conf
-rw-r--r-- 1 root root 1.2K Mar  8 19:24 10-evdev.conf
-rw-r--r-- 1 root root 1.4K May 17  2016 10-quirks.conf
-rw-r--r-- 1 root root  590 Mar  3  2016 11-evdev-quirks.conf
-rw-r--r-- 1 root root  364 Mar  3  2016 11-evdev-trackpoint.conf
-rw-r--r-- 1 root root 1.8K Mar  3  2016 50-synaptics.conf
-rw-r--r-- 1 root root  115 Mar  3  2016 50-vmmouse.conf
-rw-r--r-- 1 root root 1.4K Mar  3  2016 50-wacom.conf
-rw-r--r-- 1 root root  590 Mar  3  2016 51-synaptics-quirks.conf
user@machine~> 

------------------------------------------------------------------


So I edit the evdev conf, because if i can get it to work there I'll be one step closer to creating a proper xorg.conf file.

user@machine~> sudo vim /usr/share/X11/xorg.conf.d/10-evdev.conf
------------------------------------------------------------------

#
# Catch-all evdev loader for udev-based systems
# We don't simply match on any device since that also adds accelerometers
# and other devices that we don't really want to use. The list below
# matches everything but joysticks.

Section "InputClass"
        Identifier "evdev pointer catchall"
        MatchIsPointer "on"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"

#########################
# I added these 3 lines #
#########################
        Option "EmulateWheel" "true"
        Option "EmulateWheelButton" "2"
        Option "Emulate3Buttons" "true"

EndSection

Section "InputClass"
        Identifier "evdev keyboard catchall"
        MatchIsKeyboard "on"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
EndSection

Section "InputClass"
        Identifier "evdev touchpad catchall"
        MatchIsTouchpad "on"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
EndSection

Section "InputClass"
        Identifier "evdev tablet catchall"
        MatchIsTablet "on"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
EndSection

Section "InputClass"
        Identifier "evdev touchscreen catchall"
        MatchIsTouchscreen "on"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
EndSection

-------------------------------------------------------------------


So then I start up a new X11 session on Virtual termial 2 ( I.E. CTRL+ALT+F2 ) and run xev to see if it worked

Output from xev
-------------------------------------------------------------------
+++++++++++++++++++++++++++
+ I press the Left Button +
+++++++++++++++++++++++++++

ButtonPress event, serial 34, synthetic NO, window 0x2a00001,
    root 0x98, subw 0x0, time 5139508, (122,112), root:(123,696),
    state 0x0, button 1, same_screen YES

ButtonRelease event, serial 34, synthetic NO, window 0x2a00001,
    root 0x98, subw 0x0, time 5139586, (122,112), root:(123,696),
    state 0x100, button 1, same_screen YES





++++++++++++++++++++++++++++
+ I press the Right Button +
++++++++++++++++++++++++++++

ButtonPress event, serial 34, synthetic NO, window 0x2a00001,
    root 0x98, subw 0x0, time 5140756, (122,112), root:(123,696),
    state 0x0, button 3, same_screen YES

ButtonRelease event, serial 34, synthetic NO, window 0x2a00001,
    root 0x98, subw 0x0, time 5140778, (122,112), root:(123,696),
    state 0x400, button 3, same_screen YES





++++++++++++++++++++++++++++
+ I press the Both Buttons +
++++++++++++++++++++++++++++

ButtonPress event, serial 34, synthetic NO, window 0x2a00001,
    root 0x98, subw 0x0, time 5141746, (122,112), root:(123,696),
    state 0x0, button 2, same_screen YES

ButtonRelease event, serial 34, synthetic NO, window 0x2a00001,
    root 0x98, subw 0x0, time 5141978, (122,112), root:(123,696),
    state 0x200, button 2, same_screen YES
-------------------------------------------------------------------


Then I run gnome-termial, type ls just to generate some text and try using the scroll wheel to scroll up.
It doesn't work. When I press both buttons it performs the paste action instead of scrolling.

3 button emulation works, but the scrollwheel emulation does not.

Why?!

---

