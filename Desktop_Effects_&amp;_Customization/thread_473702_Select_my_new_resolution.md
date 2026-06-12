---
title: "Select my new resolution?"
date: 2007-06-14
forum: Desktop Effects &amp; Customization
---

### Post by derby007 on 2007-06-14
I've used the utility/program 915Resolution to change my resolution, but I still only have the 3 standard options (& not my new option) when I go into the 'Menu' & 'Screen Resolution' !! How do I add my new resolution into this menu?

---

### Post by Irti on 2007-06-14
type in gksudo gedit /etc/X11/xorg.conf in your terminal........go to the monitor section and change the resolution in the red font ( i have pasted it in the red color) change it to whatever resolution you want....

Section "Monitor"
    Identifier     "MCM 171E"
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "nVidia Corporation G71 [GeForce 7300 GS]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation G71 [GeForce 7300 GS]"
    Monitor        "MCM 171E"
    DefaultDepth    24
    Option         "AddARGBVisuals" "True"
    Option         "NoLogo" "True"
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       1
        Modes      "1024x768" "800x600" "720x450" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1024x768" "800x600" "720x450" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1024x768" "800x600" "720x450" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1024x768" "800x600" "720x450" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1024x768" "800x600" "720x450" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes     [COLOR="Red"] "1152x864[/COLOR]" "800x600" "720x450" "640x480"
    EndSubSection
EndSection

---

### Post by derby007 on 2007-06-14
Cheers, I had tried that last nite, but unfortunatley it doesnt work. I also tried 'Virtual 1152 864' (as was suggested in a previous thread), but with no success....

---

### Post by Ub1476 on 2007-06-14
You've got graphics driver installed, right?

---

### Post by derby007 on 2007-06-15
OK I managed to get something working, I now have an extra option in the 'Resolution' menu, ie. 1152*864', and it lets me select it, but I can only see ~75% of my desktop, ie. I have to scroll with the mouse to see parts of the desktop that are missing !! what am I doing wrong or overlooking?

---

### Post by fulanodetal316 on 2007-06-15
I am having the same problems with my nVidia card. I finally got it working and it shows any resolution greater than 800x600 by using that scrolling trick. I just upgraded from Windows so I know my graphics card and monitor can handle the higher resolutions

---

