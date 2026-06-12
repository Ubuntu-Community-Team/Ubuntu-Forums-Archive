---
title: "How to make GDM stop using 1280x1024"
date: 2008-12-31
forum: Desktop Environments
---

### Post by Underpants on 2008-12-31
```

Section "Device"
        Identifier      "Configured Video Device"
        Driver          "vesa"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
        HorizSync 30-63
        VertRefresh 56-76
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        SubSection "Display"
                Depth           16
                Modes           "1024x768"
        EndSubSection
EndSection
```


I'm trying to set up my headless servers to use 1024x768 (I only connect through VNC)

What do I need to change in my xorg.conf file to make GDM stop using 1280x1024?

---

