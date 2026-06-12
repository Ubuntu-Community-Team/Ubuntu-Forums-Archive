---
title: "a wierd fglrx problem"
date: 2006-12-19
forum: Desktop Environments
---

### Post by Hablas on 2006-12-19
I finally got the 3D support working on my ubuntu (gnome as X).

Then i tryed to get the 3D-desktop working, and i googled and found a page where it sayed that you have to install ati's own driver from the binary file.

Well, I did as instructed. (sorry, cant find the site anymore or i would have posted it's link here.)

When things didn't go correctly i stopped installing the drivers and tryed to return the backups.
Now there are these errors that i cant get fixed:

error 1:
> $ modprobe fglrx
FATAL: Error running install command for fglrx

error 2:
command "lsmod" doesen't find fglrx

error 3:

> $ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)

This comes even when i have added the Extensions part in the end of the xorg.conf:

Section "Extensions"
        Option      "Composite" "Disable"
EndSection

Now I cant get the 3D support back, being the direct symptom of fglrx not being in use.

I have this in my xorg.conf:

> Section "Device"
        Identifier  "ATI Technologies, Inc. ATI Default Card"
        Driver      "vesa"
        BusID       "PCI:1:0:0"
EndSection

Section "Device"
        Identifier  "aticonfig-Device[0]"
        Driver      "fglrx"
        Option      "VideoOverlay" "on"
        Option      "OpenGLOverlay" "off"
EndSection


I believe that all of these are connected. I also believe that i didnt get the modules right.
Hope someone has any idea from where to start looking. :(

---

### Post by pormogo on 2006-12-19
For future reference you do not have to uninstall the driver in order to use a new one, you can simply specify a new driver in /etc/X11/xorg.conf. Go ahead and post the contents on our /etc/X11/xorg.conf did you install fglrx driver via apt or did you use the ati package generator.

---

### Post by Hablas on 2006-12-20
Here's the xorg.conf:

```
Section "Device"
        Identifier  "ATI Technologies, Inc. ATI Default Card"
        Driver      "vesa"
        BusID       "PCI:1:0:0"
EndSection

Section "Device"
        Identifier  "aticonfig-Device[0]"
        Driver      "fglrx"
        Option      "VideoOverlay" "on"
        Option      "OpenGLOverlay" "off"
EndSection

Section "Screen"
        Identifier "Default Screen"
        Device     "ATI Technologies, Inc. ATI Default Card"
        Monitor    "SyncMaster"
        DefaultDepth     24
        SubSection "Display"
                Depth     1
                Modes    "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     4
                Modes    "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     8
                Modes    "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     15
                Modes    "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     16
                Modes    "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     24
                Modes    "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
EndSection

Section "Screen"
        Identifier "aticonfig-Screen[0]"
        Device     "aticonfig-Device[0]"
        Monitor    "aticonfig-Monitor[0]"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection
EndSection

Section "DRI"
        Mode         0666
EndSection

Section "Extensions"
        Option      "Composite" "Disable"
EndSection
```

The site said to remove the old ones, so I did :)

Downloaded the ati package generator from ati's homepage and installed it.

---

### Post by pormogo on 2006-12-26
Sorry I was out doing the holiday thing, that looks to be correct. try running 

*dmesg |grep fglrx*

to see if there was an error at boot.

---

### Post by Hablas on 2006-12-26
Oh yeah, i got the problem fixed. 
The module was broken so i used apt-get --reinstall xorg-driver-fglrx command to reinstall it. I reintalled the xorg-server module too and it works now.

Thanks for your posts.

---

