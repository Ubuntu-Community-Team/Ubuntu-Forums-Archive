---
title: "Upgraded Beryl Broken"
date: 2007-02-04
forum: Desktop Environments
---

### Post by Razer on 2007-02-04
I upgraded beryl from version .1.1 to the newest one and beryl works but beryl manager and beryl settings manager won't work.
When I type "beryl-manager" into the terminal, I get a drop down box that allows me to select emerald, beryl settings manager, etc. But I can't open beryl settings manager.
I get this when I type "beryl settings manager" into the terminal.
```
razer@razer-desktop:~$ beryl settings terminal
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : XGL

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Checking for non power of two texture support   : passed
Checking maximum texture size                   : passed (4096x4096)

beryl: No XKB extension
XIO:  fatal IO error 104 (Connection reset by peer) on X server ":0.0"
      after 137 requests (136 known processed) with 0 events remaining.
razer@razer-desktop:~$ 
razer@razer-desktop:~$ 
```

When I type "beryl-settings" into the terminal I get this. 
```

razer@razer-desktop:~$ beryl-settings
Traceback (most recent call last):
  File "/usr/bin/beryl-settings", line 22, in <module>
    import berylsettings
ImportError: No module named berylsettings
razer@razer-desktop:~$ 
```

Please help me to get my beryl manager and settings manager back.

---

### Post by gp2x on 2007-02-04
got something similar here - beryl-manager works for me, but:


```
simon@beast:~$ beryl-xgl 
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : XGL

Checking Display :1.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Segmentation fault (core dumped)
```


ouch - I cant live without beryl now!

---

### Post by gp2x on 2007-02-04
I downgraded all the beryl (but not the emerald) packages to the last version and it fired back into life.

---

### Post by Razer on 2007-02-04
What commands did you use to downgrade beryl and to what version did you downgrade it to?

---

### Post by raul_ on 2007-02-04
Open Synaptic and then search for "beryl" and downgrade every package (ctrl+e to force version) to the one before (1.99.2 i think)

---

### Post by Razer on 2007-02-04
Thanks I downgraded to .1.1 and everything is back to normal.

---

### Post by AstarothCY on 2007-02-04
Also downgraded, to 1.99.2, works (mostly) fine.

Make sure you do a complete removal of all the components before installing the older version, I was getting errors in Synaptic before I did that.

---

