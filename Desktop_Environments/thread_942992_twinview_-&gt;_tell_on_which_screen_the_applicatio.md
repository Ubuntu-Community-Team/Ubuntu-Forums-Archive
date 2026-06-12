---
title: "twinview -&gt; tell on which screen the application should be started"
date: 2008-10-09
forum: Desktop Environments
---

### Post by Okar on 2008-10-09
hi,
I am using Kubuntu with 2 monitors via Twinview.
if I start an application through the terminal is there a way of telling on which screen this should be opened?
with seperate xscreens you could just set the DISPLAY env variable, though when using twinview you only got one big screen.

---

### Post by Chad.S on 2008-10-09
Do you mean you just want to change the screen on which the apps normally launch on? If so, you will need to edit the /etc/X11/xorg.conf file and add the following option line (edit it to match your screen names in xorg.conf).

The quote comes from ....

[http://http.download.nvidia.com/XFree86/Linux-x86/1.0-9626/README/appendix-d.html](http://http.download.nvidia.com/XFree86/Linux-x86/1.0-9626/README/appendix-d.html)

> 
Option "TwinViewXineramaInfoOrder" "string"

    When the NVIDIA X driver provides TwinViewXineramaInfo (see the NoTwinViewXineramaInfo X config option), it by default reports the currently enabled display devices in the order "CRT, DFP, TV". The TwinViewXineramaInfoOrder X config option can be used to override this order.

    The option string is a comma-separated list of display device names. The display device names can either be general (e.g, "CRT", which identifies all CRTs), or specific (e.g., "CRT-1", which identifies a particular CRT). Not all display devices need to be identified in the option string; display devices that are not listed will be implicitly appended to the end of the list, in their default order.

    Note that TwinViewXineramaInfoOrder tracks all display devices that could possibly be connected to the GPU, not just the ones that are currently enabled. When reporting the Xinerama information, the NVIDIA X driver walks through the display devices in the order specified, only reporting enabled display devices.


    Examples:

            "DFP"
            "TV, DFP"
            "DFP-1, DFP-0, TV, CRT"

    In the first example, any enabled DFPs would be reported first (any enabled CRTs or TVs would be reported afterwards). In the second example, any enabled TVs would be reported first, then any enabled DFPs (any enabled CRTs would be reported last). In the last example, if DFP-1 were enabled, it would be reported first, then DFP-0, then any enabled TVs, and then any enabled CRTs; finally, any other enabled DFPs would be reported.

    Default: "CRT, DFP, TV"


---

### Post by Okar on 2008-10-10
no, I want to write a script that launches different applications, on different screens,
though I don't know how to achieve that with kde and twinview.
under gnome with different xscreens I made something like this:
```
DISPLAY=':0.0'
launchapp1
launchapp2
DISPLAY=':0.1'
launchapp3
```

tough I don't want to use different xscreens under kde.

---

