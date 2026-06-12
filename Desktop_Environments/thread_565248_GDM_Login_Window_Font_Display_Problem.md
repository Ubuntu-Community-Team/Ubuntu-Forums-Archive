---
title: "GDM Login Window Font Display Problem"
date: 2007-10-02
forum: Desktop Environments
---

### Post by Linfreak on 2007-10-02
I am getting extra large fonts in my gdm login window... (see screenshots) and i think the issue may be related to my nvidia driver.. NVIDIA-Linux-x86-1.0-7185-pkg1.. coz its happening after its installation.. and gdm was working with the correct font size with nv driver.. what may be the problem..

this is my xorg.conf...

Section "Files"
Fontpath "/usr/share/fonts/X11/misc"
Fontpath "/usr/share/fonts/X11/cyrillic"
Fontpath "/usr/share/fonts/X11/100dpi/:unscaled"
Fontpath "/usr/share/fonts/X11/75dpi/:unscaled"
Fontpath "/usr/share/fonts/X11/Type1"
Fontpath "/usr/share/fonts/X11/100dpi"
Fontpath "/usr/share/fonts/X11/75dpi"
# path to defoma fonts
Fontpath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
Load "bitmap"
Load "ddc"
# Load "dri"
Load "extmod"
Load "freetype"
Load "glx"
Load "int10"
Load "vbe"
EndSection

Section "InputDevice"
Identifier "Generic Keyboard"
Driver "kbd"
Option "CoreKeyboard"
Option "XkbRules" "xorg"
Option "XkbModel" "pc105"
Option "XkbLayout" "us"
EndSection

Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/psaux"
Option "Protocol" "ImPS/2"
Option "ZAxisMapping" "4 5"
Option "Emulate3Buttons" "true"
EndSection

Section "Device"
Identifier "Generic Video Card"
Driver "nvidia"
Busid "PCI:1:0:0"
Option "RenderAccel" "true"
Option "NoLogo" "True"
Option "AllowGLXWithComposite" "True"
EndSection

Section "Monitor"
Identifier "Generic Monitor"
Option "DPMS"
Horizsync 30-75
Vertrefresh 50-160
EndSection

Section "Screen"
Identifier "Default Screen"
Device "Generic Video Card"
Monitor "Generic Monitor"
Defaultdepth 24
SubSection "Display"
Depth 1
Modes "1280x960" "1024x768" "800x600"
EndSubSection
SubSection "Display"
Depth 4
Modes "1280x960" "1024x768" "800x600"
EndSubSection
SubSection "Display"
Depth 8
Modes "1280x960" "1024x768" "800x600"
EndSubSection
SubSection "Display"
Depth 15
Modes "1280x960" "1024x768" "800x600"
EndSubSection
SubSection "Display"
Depth 16
Modes "1280x960" "1024x768" "800x600"
EndSubSection
SubSection "Display"
Depth 24
Modes "1280x960" "1024x768" "800x600"
EndSubSection
EndSection

Section "ServerLayout"
Identifier "Default Layout"
screen "Default Screen"
Inputdevice "Generic Keyboard"
Inputdevice "Configured Mouse"
EndSection

Section "DRI"
Mode 0666
EndSection

Section "Extensions"
Option "Composite" "enable"
EndSection...

PS: I m using Ubuntu Feisty upgraded to Ubuntu Studio.. and that NVIDIA driver works fine for my Debian and Mandriva...

---

### Post by smyrna112 on 2007-10-31
Same Problem. Its a bug.

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/107320](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/107320)

BTW: what theme you have installed!

---

### Post by smyrna112 on 2007-10-31
> **smyrna112 said:**
> Same Problem. Its a bug.

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/107320](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/107320)

BTW: what theme you have installed!

Update: I have seemed to fix mine. This might not be recomended but i went to 

System-> Administration-> Software Sources

Then under the Updates Tab I enabled Pre-Releases then did a software update all is working for me.

Remember the Pre-Releases are NOT FINAL and may be buggy!! These are proposed updates.

---

