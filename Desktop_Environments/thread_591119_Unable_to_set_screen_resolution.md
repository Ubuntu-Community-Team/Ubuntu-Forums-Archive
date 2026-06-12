---
title: "Unable to set screen resolution"
date: 2007-10-25
forum: Desktop Environments
---

### Post by aa310 on 2007-10-25
I am a big fan of ubuntu but not an expert in linux!

I have come across the following problem. everything is working fine appart from my resolution.

I have a SONY SDM S94 connected with dvi cable to PCI-E NVIDIA 6600GT grapgics card.

I want a resolution of 1280 x 1024 but cant do it.

Any help would be much appreciated.

Thank you very much in advance for your time and effort

---

### Post by Steve1961 on 2007-10-25
Just type the following in a terminal:

sudo gedit /etc/X11/xorg.conf

Make sure 1280x1024 is in this section:

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation NV43 [GeForce 6600 GT]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection


Save and close the file and restart x by ctrl-alt-backspace

---

### Post by aa310 on 2007-10-25
I am trully in debt.

Thank you very much for your time

Take care

---

### Post by Steve1961 on 2007-10-25
Glad it worked for you :)

---

