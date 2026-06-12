---
title: "Panel and Desktop Becomes Disabled"
date: 2009-06-05
forum: General Help
---

### Post by unleadedblues on 2009-06-05
Once every week or so the top panel and desktop becomes 'disabled'.  The system is running just fine but I can't use the Applications Menu or any of the icons I have pinned to the panel to start any programs.  The "Log Off" button and desktop don't work either.

Has anyone else encountered this?  If I can provide any further information, please let me know.

---

### Post by Legace on 2009-06-05
Are you using nVidia/ATi drivers?

Are you using Compiz?

---

### Post by unleadedblues on 2009-06-05
Yes, I am using nVidia drivers with an nVidia Quadro NVS 290 (rev a1). 

OS is Linux dev 2.6.24-24-generic #1 SMP x86_64 GNU/Linux


Section "Device"
    Identifier     "nVidia Corporation NVIDIA Default Card"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation NVIDIA Default Card"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "AddARGBVisuals" "True"
    Option         "AddARGBGLXVisuals" "True"
    Option         "NoLogo" "True"
    SubSection     "Display"
        Depth       24
        Modes      "nvidia-auto-select"
    EndSubSection
EndSection

---

