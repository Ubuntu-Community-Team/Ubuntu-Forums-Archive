---
title: "Synaptic Touchpad in Intrepid"
date: 2008-11-29
forum: Desktop Environments
---

### Post by kneewax on 2008-11-29
In Hardy I had disabled my touchpad using the gsynaptics tool.  Since upgrading to hardy this tool no longer works.  It claims I need to re-add the lines to my xorg.conf  - when I try to do this I find the whole file has been commented out by intrepid saying the seetings are no longer needed - if I put the gsynaptics in there - it makes no difference so I guess the file is redundant.  

Does anyone know how I can disable the pad?

---

### Post by mali2297 on 2008-11-29
Have you tried enabling SHMConfig as decribed [here](https://help.ubuntu.com/community/SynapticsTouchpad#shmconfig)?

Alternatively, you can try this [tip](http://ubuntuforums.org/showpost.php?p=5694509&postcount=13).

---

### Post by gib2800 on 2008-12-06
If you're using Ubuntu Intrepid, touchpad can be configured by going to "Control Center", selecting "Mouse Preferences", clicking the "Touchpad" tab and selecting or deselecting either "Enable Touchpad" or "Enable Mouseclicks with Touchpad"

In Kubuntu Intrepid, 
[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=968668]("http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=968668")

Intrepid doesn't use Xorg to configure touchpad but instead seems to use Hal.

---

