---
title: "Beryl freezes everything!"
date: 2007-02-12
forum: Desktop Environments
---

### Post by kramer65 on 2007-02-12
Hello,

I just wanted to install beryl in gnome (ubuntu 6.06). I used the explanation on [http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Dapper_with_AIGLX](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Dapper_with_AIGLX) and I think I got it installed, but when I start it by typing "beryl-manager" in the terminal I do get the red juwel in the thing on the right top (how do you call that..?), but everything freezes. I can actually click the red juwel and go to settings or something, but for the rest no other window works anymore. I need to restart to (or log out) to resolve this.

Does anybody know what's wrong?

---

### Post by Paerez on 2007-02-12
what is output to the terminal?

---

### Post by Sqwishy on 2007-02-12
I'm pretty sure it's not actuall freezing it just doesn't load the window borders. So you right click on the beryl icon, the juwel :P and set your window decorator to emerald, if it is already there try reloading the window decorator.

---

### Post by kramer65 on 2007-02-12
True. It is not freezing. I can now write a response. Currently the terminal is still partly over FF. The output to the terminal is 

Xlib: extension "XFree86-DRI" missing on display ":0.0".
XGL Absent, checking for NVIDIA
Nvidia Absent, assuming AIGLX
Beryl:GLX_EXT_texture_from_pixmap is missing
beryl: Failed to manage screen: 0
Beryl No manageable screens found on display :0.0
XGL Absent, checking for NVIDIA
Nvidia Absent, assuming AIGLX
beryl: GLX_EXT_texture_from_pixmap is missing
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :0.0

If I right click on the beryl icon I cannot select the window decorator. If I mouseover it, it stays grey. Also the reload window decorator is grey.

---

### Post by Paerez on 2007-02-12
Hmm it seems the nvidia drivers weren't installed correctly. I would look for a nvidia/beryl guide and make sure you follow it perfectly.

---

### Post by shareMenaPeace on 2007-02-12
You can try to just restart beryl (quiet) than run beryl-manager from temrinal to restart and choose beryl as window manager.

Maybe you need these settings in xorg.conf as well.

```
Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection
Section "Device"
    Identifier     "NVIDIA Corporation NVIDIA Default Card"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NVIDIA Default Card"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "RenderAccel" "true"
    Option         "AllowGLXWithComposite" "true"
    Option         "backingstore" "true"
    Option         "AddARGBGLXVisuals" "True"
    Option         "TripleBuffer" "true"
    Option         "DRI" "true"
    SubSection     "Display"
        Depth       1
        Modes      "1280x800" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x800" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x800" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x800" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x800" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x800" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection
```

btw i first had most "true" settings under device, but after envy reinstalled my nvidia drivers it set iit as you see - works.

Envy nvidia install script (Also good fix for none booting systems due to kernel update).
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

