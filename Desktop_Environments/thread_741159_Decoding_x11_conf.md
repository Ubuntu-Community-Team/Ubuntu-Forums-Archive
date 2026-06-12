---
title: "Decoding x11 conf"
date: 2008-03-31
forum: Desktop Environments
---

### Post by CoffeeBreath on 2008-03-31
Can someone explain to me what's being said in my x11 conf file. What's the difference between monitor and screen. Also- How can I tell the true refresh rates of my screen? Look like linux just picked a generic.

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-51
        VertRefresh     43-60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "nVidia Corporation MCP51 PCI-X GeForce Go 6100"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

---

### Post by process91 on 2008-03-31
The Monitor is to describe the hardware limitations (refresh rates) of the monitor and allow any other features (i.e. energy saving) specific to the monitor to be enabled.

The Screen section points to the monitor it's related to on this line

*Monitor         "Generic Monitor"*

And among other things it sets the resolutions allowed.

Currently xorg is using default settings. In Ubuntu you can make this more specific to your monitor by using displayconfig-gtk. This is in the menus, but the placement has been switched around. You can check in System->Preferences and System->Administration, most recently Hardy includes it in Applications->Other. Better yet, run it from the command line with this command

```
gksudo displayconfig-gtk
```

Once you get it running change your monitor model and apply the settings. Restart X by hitting ctrl+alt+backspace.

---

