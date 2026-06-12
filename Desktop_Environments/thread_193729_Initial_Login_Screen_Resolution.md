---
title: "Initial Login Screen Resolution"
date: 2006-06-10
forum: Desktop Environments
---

### Post by kdeaner on 2006-06-10
Hello,
I've had Ubuntu 6.06 installed for a few days now and I love it!. I've managed to get everything done that I wanted too, from installing the latest ATI drivers to configuring a VNC server to run on a port other that the default. However, I have one nagging issue that I can't seen to correct. I also can't seem to find any information on the web to correct it.

When the first instance of Gnome loads, the login screen, it is at a different resolution and refresh rate than my desktop. My desktop is perfect at 1024x768x32 at 85 Hz. My xorg.conf is correct, at least for my user name anyway. How can I alter the login screen resolution? Way back when, in NT4, to change the login screen resolution, one had to alter a registry setting in HKEY_LOCAL_MACHINE. Now, I know Linux has no registry but is there another file somewhere that holds the settings for the login screen that performs a task similar to xorg.conf? I've been working in SCO Unix and Debian Linux environments for several years and I know my way around the shells but I'm very new to Gnome. Any help would greatly be appreciated.
Thanks,
Ken

---

### Post by kdeaner on 2006-06-10
Nevermind. I realized that I was missing a Modes line under the Screen section of /etc/X11/xorg.conf. I just added:

Modes    "1024x768"

Once I rebooted all is OK.

The whole section looks like this:

Section "Screen"
        Identifier "aticonfig-Screen[0]"
        Device     "aticonfig-Device[0]"
        Monitor    "aticonfig-Monitor[0]"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
                Modes    "1024x768"
        EndSubSection
EndSection

Maybe this will help someone else...

---

