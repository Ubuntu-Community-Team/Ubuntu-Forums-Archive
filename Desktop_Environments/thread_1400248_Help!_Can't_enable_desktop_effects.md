---
title: "Help! Can't enable desktop effects"
date: 2010-02-06
forum: Desktop Environments
---

### Post by eurodaze on 2010-02-06
Hiya,

Can anyone help? I am an absolute newbie and I can't get any desktop effects to enable. I ran Compiz check and this is what it tells me...

Distribution:          Ubuntu 9.10
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation C77 [GeForce 8200] (rev a2)
 Driver in use:         nvidia
 Rendering method:      Nvidia

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [FAIL]
 Checking for non power of two support...          [FAIL]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [FAIL]
 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: Unable to detect maximum 3D texture size 

I don't know what thus means or how to fix it... all those FAILS can't be good though...

Suggestions welcome!

---

### Post by cc272 on 2010-02-06
I think maybe there is a bug of sorts I did the kernel update last night and now my compiz and emerald are both on the fritz, the update dropped my GUI completely and i had to reinstall All the Nvidia files and start over. i may just be going back to mandriva since that just works. I also noticed the npviewer problem has become worse with the new update since firefox keeps freezing. as soon as i kill npviewer i can  browse again until it starts again, i have been using Opera and that seems to work fine no hangups.

---

### Post by I Forgot My Username on 2010-02-06
Have you installed the driver for your graphics card?  nVidia is proprietary, so Ubuntu won't install it automatically.  If you haven't go to System->Administration->Hardware Drivers, if there's any drivers listed there, install them.  If "Hardware Drivers" isn't on the menu, run
```

sudo apt-get install jockey-gtk

```Hope that helps,
Tyler

---

### Post by eurodaze on 2010-02-07
All drivers are in use and up to date... uninstalled an reistalled a million times.... what if I just bought a new graphics card?

Any suggestions on which are DEFINATELY compatible with Karmic?

---

