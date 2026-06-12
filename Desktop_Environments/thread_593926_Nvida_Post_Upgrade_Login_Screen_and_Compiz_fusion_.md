---
title: "Nvida Post Upgrade Login Screen and Compiz fusion Problems &amp; how to fix them"
date: 2007-10-27
forum: Desktop Environments
---

### Post by StevenHarper on 2007-10-27
After upgrading to 7.10 from 7.04 I had found 2 problems

[LIST=1]
[*]My Login Screen resolution was very high (2048 x 1536)
[*]When I enabled desktop effects the Window Decorators (title bars) were missing
[/LIST]

The problem was that I had used the Nvidia Settings panel to set my resolution in 7.04

To Fix the window decorators missing I had to add the following to my **/etc/X11/xorg.conf**

backup the current one

```
sudo cp  /etc/X11/xorg.conf  /etc/X11/xorg.conf_BAK
```

Edit the current one

```
sudo gedit /etc/X11/xorg.conf
```

Add the options
[B]Option "AddARGBVisuals" "True"
Option "AddARGBGLXVisuals" "True"[/B]

```
Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "Unknown"
    [COLOR="Red"]Option "AddARGBVisuals" "True"
    Option "AddARGBGLXVisuals" "True"[/COLOR]
EndSection
```

to make the changes take effect either re-boot the box, or press - CTRL+ALT+Backspace



Ok next one the Ubuntu Login Screen;

Again I had to modify my 

 **/etc/X11/xorg.conf**

backup the current one

```
sudo cp  /etc/X11/xorg.conf  /etc/X11/xorg.conf_BAK
```

Edit the current one

```
sudo gedit /etc/X11/xorg.conf
```

Now below is mine, because I used nvidia-settings, I have meta modes this complicates it a bit

The Login screen picks the first entry in the Screen modes for the Default Depth
Unless is has Metamodes, if you have metamodes, then it picks the first one of them

As you can see my meta mode is **nvidia-auto-select +0+0**

```
Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "metamodes" "[COLOR="Red"]nvidia-auto-select +0+0[/COLOR];1600x1200_85 +0+0"
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection
```

This meant that the nvidia auto mode chose the highest resolution possible 2048 x 1536, even though it wasn't in my list at all.

To fix this i moved the **1600x1200_85 +0+0** to the beginning of the list.

```
Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "[COLOR="Red"]metamodes" "1600x1200_85 +0+0[/COLOR]; nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

```

to make the changes take effect either re-boot the box, or press - CTRL+ALT+Backspace


I hope this helps someone

Steve

---

