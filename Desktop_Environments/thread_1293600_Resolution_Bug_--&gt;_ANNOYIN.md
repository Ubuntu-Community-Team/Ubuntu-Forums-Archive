---
title: "Resolution Bug --&gt; ANNOYIN"
date: 2009-10-17
forum: Desktop Environments
---

### Post by abdusamed on 2009-10-17
let keep it simple shall we?

whenever i reboot.. my resolution on xubuntu 9.04 ALWAYS used to go after reboot back to the original resolution 800x600.. But after searching for a while.. i was able to solve it this on terminal ```
 gksudo mousepad /etc/X11/xorg.conf 
``` and adding the bold bit part ```
 Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    [B]SubSection "Display"
        Depth 24
        Modes "1024x768"
    EndSubSection[/B]
EndSection 

```i however wasn't able to solve the other resolution problem.. which GETS On my nerve! the problem is that the option to change the different resolution simple DISAPPEARS.. i get the options to choose the resolution below 800x600! i need 1024x768! i also did find the solution for it before... simple plug in the iso and reboot.. but i want to solve the problem from the dman ROOTS! like..right now..im workin on 800x600 and don't feel like rebootin!

---

