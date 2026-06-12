---
title: "completely disabling composite in KDE for use of NVIDIA vision 3D"
date: 2016-05-09
forum: Desktop Environments
---

### Post by schockschwerenot on 2016-05-09
hi guys,

since a couple of years (since ubuntu 10.04/gnome) i'm using a dual screen system together with the NVIDIA 3D vision shutter system (on an NVIDIA Quadro FX 3800 graphics card along with, lastly, the NVIDIA proprietary driver 340.96). 

having installed Ubuntu-14.04 two years ago i needed to switch to KDE in order to be able to activate stereoscopic viewing. that is in detail, i installed ubuntu-gnome first, afterwards a added the XFCE, LXDE, and, finally, the KDE desktop on top of that until i was successful. in particular, i needed to deactivate composite in the KWIN settings. in nvidia-settings (xorg.conf) i always have (need) the additional lines:

```
Section "Extensions"
    Option         "Composite" "Disable"
EndSection
```

and, in the screen section these ones among others:

```
Option         "AllowDFPStereo" "1"
Option         "UBB" "1"
Option         "Stereo" "10"
```

now, two years later i directly installed **K**ubuntu-16.04 rather than **U**buntu and, again, toggled off the setting related to composite starting during system start. after system start i do realize that desktop effects (transparency, etc.) indeed are off and 3D stereoscopy works fine. however, when either hitting ALT-F2, clicking the "KDE start button", or clicking on the background of the secondary screen, both entire screens turn black. i than need to hit ESC or "somewhere" on the primary screen in order to get rid of the black screen.

it somehow seems, that some 3D effects are still active. following the hints of some web site, i installed and started the compiz manager

```
sudo apt-get install compizconfig-settings-manager
ccsm &
```

however, any compiz effect is deactivated here as well. does anyone know a solution to this problem? do you think it makes any difference if installing **U**buntu-16.04 and the KWIN desktop on top of that as i had done 2 years before?

many thanks in advance

---

### Post by T.J. on 2016-05-09
Kde does not use Compiz. It's effects are built into Kwin. You can disable them via the settings manager.  It can simulate some effects even with Composite disabled by using XRender.

---

### Post by schockschwerenot on 2016-05-11
ok. got it. stereoscopy works "fine" now on 16.04. what i did is: installing Ubuntu-16.04 and using a copy of my old home partition (of 14.04) for the new OS. then installing gnome and afterwards plasma-desktop. i don't even need to add the lines 

> Section "Extensions"     Option         "Composite" "Disable"
EndSection

anymore. i guess it's actaully just a matter of setting, but no one was able so far to tell me what exactly to do.

---

