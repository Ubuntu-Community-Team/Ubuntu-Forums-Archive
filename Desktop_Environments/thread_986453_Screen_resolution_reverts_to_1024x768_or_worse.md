---
title: "Screen resolution reverts to 1024x768 or worse"
date: 2008-11-18
forum: Desktop Environments
---

### Post by jhenager on 2008-11-18
This happened in 8.04 and also 8.10. I did a clean install of Intrepid, so I know this is not a carryover from Hardy.
Sometimes, I can log out and back in, and it is fixed. Sometimes, I have to shut down and restart or a combination of that and logging out. The almost always sure fire fix is to kill Desktop Effects and then re-enable them.
Using an integrated nVidia 6xxx video card.

Anyone have a better idea how to keep this from happening?

---

### Post by inobe on 2008-11-18
open nvidia settings with sudo, this way your adjustments will stick.

```
sudo nvidia-settings
```

---

### Post by jhenager on 2008-11-22
> **inobe said:**
> open nvidia settings with sudo, this way your adjustments will stick.

```
sudo nvidia-settings
```

This helped somewhat, allowing me to get to 1152x864, but higher resolutions previously available are still not there.
This did help answer why I was getting error messages attempting to save configuration without using sudo, and for that, I thank you.

---

### Post by inobe on 2008-11-23
if you are not getting max resolution' this could be due to missing modes, you will need to post your xorg.config file along with make/ model of your monitor.

do this in terminal

```
gksudo gedit /etc/X11/xorg.conf
```

copy and paste that with the use of forum code#

post back with the needed information.

---

### Post by jhenager on 2008-11-25
Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "ING"
    HorizSync       30.0 - 95.0
    VertRefresh     50.0 - 180.0
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    Option         "NoLogo" "True"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6150SE nForce 430"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
EndSection

Section "Screen"

# Removed Option "metamodes" "nvidia-auto-select +0+0"
# Removed Option "metamodes" "1152x864 +0+0"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "1600x1200 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
More information - it may actually have been a hardware issue. The monitor is an old Intergraph 19" CRT, and it started clicking and resetting itself. It is now in the garage, and will be going to the recyclers soon.
Expecting a new 22" LCD tomorrow. We'll see if this is the end of the random resolutions.

---

### Post by Spartachris on 2009-02-01
Same problem...but:

I tried using

```
sudo nvidia-settings
```

and it worked until I logged out and restarted, and it reverted back to 1024x768

---

### Post by andrea000 on 2009-02-02
If you have tryed installing the newest drivers and that didn't work try
envy if your running hardy i don't know about Intrepid i thank it works 
on Intrepid i had about the same problem and it fixed mine

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

