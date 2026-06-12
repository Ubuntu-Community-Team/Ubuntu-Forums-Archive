---
title: "&quot;NoDFPNativeResolutionCheck&quot;"
date: 2007-06-23
forum: Desktop Environments
---

### Post by Sunforge on 2007-06-23
I'd been playing around with dual booting Vista and Feisty and made the mistake of not backing up my xorg.conf file when I nuked everything to start with a clean slate. This caused no end of problems because I had to go back to square one and wrestle with the fact that the NVIDIA driver doesn't want to run most flat panel monitors at native resolution (as far as I can tell from the posts on the forums). Anyway after much head scratching I remembered the magic command, stuffed it into xorg.conf and after a quick start and stop of GDM got my native res back.

For me the magic command is:
 "ModeValidation" "NoDFPNativeResolutionCheck""

Now this set me to thinking: this command doesn't appear to do me any harm, so what are the reasons for leaving it out ?

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "ModeValidation" "NoDFPNativeResolutionCheck"
    Option         "metamodes" "1600x1200,1600x1200;1280x1024,1280x1024"

---

