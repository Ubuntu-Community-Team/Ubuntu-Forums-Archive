---
title: "poor screen resolution"
date: 2007-10-30
forum: Desktop Environments
---

### Post by egrog52 on 2007-10-30
Have just put Feisty on a Dell Optiplex gx240 and am only getting a screen resolution of 800x600 is there any way of improving this?

---

### Post by taurus on 2007-10-30
What graphic card do you have in that machine?  You probably need to install a driver for it.

---

### Post by egrog52 on 2007-10-30
Just looked it is a Rage 128 Pro Ultra TF

---

### Post by erginemr on 2007-10-30
Besides the driver, you may try checking your screen section of "/etc/X11/xorg.conf" file. Mine is as follows:
"Section "Screen"
        Identifier      "Default Screen"
        Device          "nVidia Corporation NV17 [GeForce4 MX 440]"
        Monitor         "SyncMaster"
        Defaultdepth    24
        SubSection "Display"
                Modes   "1024x768"      "800x600"       "640x480"
        EndSubSection
EndSection"

and I can use 1024x768, 800x600 or 640x480 as a result.

You may try copying your xorg.conf file first:
"sudo cp /etc/X11/xorg.conf /etc/X11/xorg.orig"

and then, change the relevant line as
...
Modes   "1024x768"      "800x600"       "640x480"
...
by using
"gksu gedit /etc/X11/xorg.conf"

Give it a try, restart the X server by "Ctrl+Alt+BackSpace" and see if you can have the other two resolutions.

---

### Post by L815 on 2007-10-30
Did you go to System > Administration > Restricted drivers manager and see if your graphics card is enabled?

---

### Post by egrog52 on 2007-10-30
it says my hardware does not need any restricted drivers

---

### Post by L815 on 2007-10-30
Hmm. Read the last post on this thread, might be of some help.

[http://ubuntuforums.org/showthread.php?t=275546](http://ubuntuforums.org/showthread.php?t=275546)

---

### Post by egrog52 on 2007-11-01
Thanks very much that sorted it.:):)

---

