---
title: "Karmic Visual Effects not working after upgrade from Jaunty"
date: 2010-02-18
forum: Desktop Environments
---

### Post by arvindp3 on 2010-02-18
I upgraded 9.04 to 9.10. After upgrade, the system was freezing after a few minutes.  
So edited compiz-manager to change compiz_name from "compiz.real" to "metacity" based on a thread on the forum.  That solved freeze problem. 

But visual effects can not now be set to Normal or Extra.   System searches for drivers and comes up with an empty drivers window.

Compiz settings through CCSM have no effect.  Under 9.04 visual effects = Extra was working with default compiz settings.


**My video card is :**
VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)

**xorg.conf exists but looks sort of empty as below:**

Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

**compiz-manager file is :**
# Ubuntu specifc compiz-manager configuration file
# goes into /etc/xdg/compiz/compiz-manager
# works with git://anongit.compiz-fusion.org/fusion/misc/compiz-manager
COMPIZ_BIN_PATH="/usr/bin/" 
PLUGIN_PATH="/usr/lib/compiz/" 
COMPIZ_NAME="compiz.real"
#COMPIZ_NAME="metacity"

I am seeing some discussion on the forums that this may be due to a intel video driver, but have no real clue how to resolve this.

Would appreciate some hints to use Compiz visual effects on Karmic.  Thanks.

---

### Post by arvindp3 on 2010-02-19
Looks like this is a reported bug... in process @ launchpad.

See bug #492271  in Launchpad.

Guess I will wait to see how that gets resolved....

---

