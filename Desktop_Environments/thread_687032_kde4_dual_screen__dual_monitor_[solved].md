---
title: "kde4 dual screen / dual monitor [solved]"
date: 2008-02-03
forum: Desktop Environments
---

### Post by gentoofrm on 2008-02-03
main screen: 1024x768 notebook lcd
second screen: 1920x1200 external lcd
graphic: intel gma 855 (i810) with 915resolution

problem: the main screen is overlapped on the second screen, making the second screen hard to use

partial solution (an extended screen, NOT an independent  2nd screen)

1) xorg.conf : Virtual screen size (2944 1200) combines the horizontal screen sizes 1024+1920 and the larger of the two vertical sizes 768 and 1200.

Section "Monitor"
        Identifier      "dell"
        Option          "DPMS"
        #Option          "Enable" "0"
        Modeline "1920x1200_60.00"  193.16  1920 2048 2256 2592  1200 1201 1204 1242  -HSync +Vsync
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation 82852/855GM Integrated Graphics Device"
        Monitor         "dell"
        DefaultDepth    24
        SubSection "Display"Section "Monitor"
        Identifier      "dell"
        Option          "DPMS"
        #Option          "Enable" "0"
        Modeline "1920x1200_60.00"  193.16  1920 2048 2256 2592  1200 1201 1204 1242  -HSync +Vsync
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation 82852/855GM Integrated Graphics Device"
        Monitor         "dell"
        DefaultDepth    24
        SubSection "Display"
        Virtual         2944 1200
        Modes           "1920x1200_60.00" "1024x768"
        EndSubSection
EndSection

2) xrandr --output VGA --off

3) xrandr --output VGA --mode 1920x1200 --pos 1024x0

4) add widgets on the second screen

You need to customize the virtual screen size in 1) and the --pos location in 3).

This might not work for systems using proprietary graphic drivers lick nvidia-settings.

Good luck!

---

### Post by ryansinn on 2008-03-25
I'm going to try this and see if it works for me... same intel video hardware (thinkpad) basically... same dual display (except I've got 1400x1050 on the laptop display)

If this works, I'm registering it as a bug with Ubuntu because under Gnome you don't have to do this ... just xrandr --output VGA --auto  
gets the external display working at 1920x1200


Nothing needs to get added to the xorg.conf

I'm running Hardy 8.04

---

### Post by maestrobwh1 on 2008-05-02
Good, because it is driving me nuts that when I launch kde3, it all works automatically, and with kde4, the panel is half way up the screen and only goes 2/3 across on my external monitor.  I am using an asus eee-pc with an external 1280x1024 monitor.  If I even dare play with the config settings, it goes to the lowest possible resolution of the laptop screen and the desktop area is unusable AND I can't seem to set it back down with any tool.  I have to copy my original xorg.conf and replace whatever it does.  I am using Gutsy for both kde3 and kde4.

I can make kde4 usable by making the panel go to the top of the screen, but oddly, the k-menu can only be pulled down to where the panel was... even though when I launch apps, they can use the whole screen, as well as widets that can be placed anywhere.  The wallpaper also makes an 800x480 rectangle in the upper left... so basically what it is doing is placing the 800x480 desktop attributes of the panel and wallpaper on top of a new desktop.  Kind of weird.  If I open systemsettings >> display, the screen flickers madly then I get the low res 600x480 screen which is horrible, and any changes I make in systemsettings --> display don't work ("APPLY" is never highlighed).

I tried to manually add lines to xorg setting up two sections for device, monitor screen, but that did the same thing.

I tried setting up dual monitors in kde3 (tried plug and play, then actual monitor make/model), when I reboot, I get the low res warning and I can't get the desktop until I restore my original xorg.conf and do a sudo dpkg-reconfigure kdm

Lastly I tried to use within kde4 "sudo displayconfig-gtk" and no changes would stick with that either.

---

