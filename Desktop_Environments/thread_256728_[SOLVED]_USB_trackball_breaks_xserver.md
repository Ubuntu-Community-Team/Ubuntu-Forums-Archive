---
title: "[SOLVED] USB trackball breaks xserver"
date: 2006-09-13
forum: Desktop Environments
---

### Post by MoebusNet on 2006-09-13
Followed "How-to Scrollwheel Effect on Logitech trackball (Marble Mouse)" by gedit /etc/X11/xorg.conf as directed:

1) Commented out from Section "Input Device" - "Configured Mouse" to EndSection.

2) At very top of xorg.conf file added code:
Input Device "USB Mouse" "CorePointer"

3) Above commented out section "Input Device" - "Configured Mouse" added a new section code:
Section "Input Device"
  Identifier "USB Mouse"
  Driver "mouse"
  Option "Device"             "/dev/input/mice"
  Option "Protocol"           "ExplorerPS/2"
  Option "Emulate3Buttons"    "true"
  Option "Buttons"            "9"
  Option "EmulateWheel"       "1"
  Option "EmulateWheelButton" "8"
  Option "YAxisMapping"       "4 5"
  Option "XAxisMapping"       "6 7"
EndSection

4) Xserver quit; had to vim /etc/X11/xorg.conf to original. Still wouldn't work; had to sudo dpkg-reconfigure -phigh xserver-xorg to recover. Back to original configuration now, but trackball doesn't work.

Any ideas? :confused: 

Trackball is a Logitech Marble Mouse with a USB connector on the cord and a facory supplied PS/2 adapter (not used). I'm running 6.06 Dapper with the i386 kernel and all the updates on a 1.4Ghz AMD K7 Thunderbird with 512MB.

---

### Post by max_dingemans on 2006-09-13
Hotplugging the trackball doesn't provide even basic funtionality?

And what I did to set up my trackman wireless optical (following the marble mouse guide) is similar to what you've done in step 3, except that I just changed the 'configured mouse' section from the default, to the following

Section "InputDevice"
        Identifier  "Configured Mouse"
        Driver      "mouse"
        Option      "CorePointer"
        Option      "Device" "/dev/input/mice"
        Option      "Protocol" "ExplorerPS/2"
        Option      "Buttons" "10"
        Option      "ZAxisMapping" "4 5"
        Option      "Emulate3Buttons" "true"
        Option      "EmulateWheel" "on"
        Option      "EmulateWheelButton" "2"
        Option      "XAxisMapping" "6 7"
        Option      "Resolution" "800"
EndSection

But if the trackball doesn't work with basic functionality from the start, that's beyond my expertise.

Edit: I just noticed that it could be important for me to note one thing. If you're planning to use my configuration on a marble mouse, you probably don't have a specific button two (unless emulating a 3 button, and pressing one and three at the same time works). Because of this, you'd need to adjust the 'emulatewheelbutton' to whichever botton worked for you (either 8 or 9 from what I understand about a marble mouse). Also, you might want to use the option 'Buttons' '9' instead of 'buttons' '10.'

---

### Post by MoebusNet on 2006-09-13
Thanks for the quick reply! I was away from the computer; sorry!

When I hot-plug the trackball into a USB port and leave the PS/2 mouse connected, the trackball seems to work (without scrolling). If I want to use the trackball only, xserver doesn't seem to want to work with BuffaloSoldier's how-to as described previously.

I first noticed this when I was listening to Live 365 with gstreamer, surfing this forum and attempting to set up gnucash. My cursor quit moving, the music quit playing and I was unable to do anything but a hard power-off with the power switch (ouch).

I'll try your configuration. Thanks for the help!

---

### Post by MoebusNet on 2006-09-13
Update: Apparently I was using wh0rd's USB modification to Buffalo Soldier's "How-to Scrollwheel Effect on Logitech trackball (Marble Mouse)" but I missed the July 28th post where Buffalo Soldier stated that he had his trackball connected by USB; I thought his was a PS/2 set-up. I was wrong.

Once I used Buffalo Soldier's original /etc/X11/xorg.conf and changed my about:config settings as he stated, all is well. Thanks for a great how-to Buffalo Soldier!!

---

### Post by Buffalo Soldier on 2006-09-13
Spread the love :)

---

