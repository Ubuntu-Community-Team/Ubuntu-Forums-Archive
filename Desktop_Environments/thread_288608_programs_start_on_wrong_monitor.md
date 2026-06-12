---
title: "programs start on wrong monitor"
date: 2006-10-30
forum: Desktop Environments
---

### Post by spacedoubtman on 2006-10-30
Hi,

I've just installed and configured ubuntu on my system and am very happy except that whenever I run a program from the main menu it starts on the wrong monitor. Is there a way in gnome to change which monitor applications start on?

This is quite annoying for me as the other monitor is my tv and I only want to watch videos on it.

I am using (all from synaptic):
gnome 2.16.1
Ubuntu 6.10 - the Edgy Eft (amd64 version)
X Window System Version 7.1.1
2.6.17-10-generic kernel
NVIDIA Linux x86_64 Kernel Module  1.0-8774

Here are some excerts from my xorg.conf:
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Device"
    Identifier     "Generic Video Card"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Generic Video Card"
    Monitor        "Generic Monitor"
    DefaultDepth   24 
    Option         "NoLogo" "True"
    Option         "TwinView" "True"
    Option         "TwinViewOrientation" "LeftOf"
    Option         "UseEdidFreqs" "True"
    Option         "MetaModes" "1280x1024,1024x768; 1152x864,1024x768; 1024x768,1024x768; 800x600,800x600"
    SubSection     "Display"
        Viewport    0 0
        Depth       24
        Modes      "1280x1024" "1152x864" "1024x768" "800x600"
    EndSubSection
EndSection


Thanks,
Adam

---

