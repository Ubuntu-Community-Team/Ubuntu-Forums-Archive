---
title: "glx fails to initialize, compiz checking for xgl on nvidia card"
date: 2007-12-27
forum: Desktop Effects &amp; Customization
---

### Post by rwilson04 on 2007-12-27
I am trying to get compiz fusion working. I think my old card, the ATI Rage 128, was too old to support it, so I replaced it with an NVIDIA FX 5200 (agp). The tutorial I followed to try to get compiz working was for the same card, but on gnome, while i am running kde. 

I am wondering if it is a problem left over from trying all kinds of things with the ati card, like maybe something incompatible is still installed. I have the nvidia driver that was installed with envy. ( nvidia-glx-new installed)

'compiz --replace' gives me this:

> Checking for Xgl: not present.
Detected PCI ID for VGA: 01:00.0 0300: 10de:0322 (rev a1) (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present.
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present.
aborting and using fallback: /usr/bin/metacity

'glxinfo' gives me this, (among other things, mostly redundant):

> Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
Xlib:  extension "GLX" missing on display ":0.0".


and 'cat /var/log/Xorg.0.log | grep glx' give me this:

> (II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules//libglx.so
(EE) Failed to load /usr/lib/xorg/modules//libglx.so
(II) UnloadModule: "glx"
(EE) Failed to load module "glx" (loader failed, 7)


and here are parts of my xorg.conf

> Section "Module"
        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
        Load    "extmod"
        Load    "freetype"
        Load    "int10"
        Load    "type1"
        Load    "vbe"
#       Load    "dri"
    Load           "glx"
EndSection


> Section "Device"
    Identifier     "NVIDIA GeForce FX 5200"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA GeForce FX 5200"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "AddARGBVisuals" "True"
    Option         "NoLogo" "True"
    Option         "RenderAccel" "True"
    Option         "AllowGLXWithComposite" "True"
    Option         "DisableGLXRootClipping" "True"
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enabled"
EndSection


Can anyone help me?

---

### Post by Forlong on 2007-12-27
It's always better to "reset" your xorg.conf when switching video cards:
Do a backup:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```
And then:
```
sudo dpkg-reconfigure xserver-xorg
```
Afterwards configure it like this:
```
sudo nvidia-xconfig --add-argb-glx-visuals -d 24
```

P.S. did you install any driver for your previous card?
And it might be helpful, to provide a link to the tutorial you used.

---

### Post by rwilson04 on 2007-12-27
That is actually the first thing I did when I put the new card in... the dpkg-reconfigure. Then I folowed the instructions for modifying xorg.conf from compiz.org/nvidia. Since I was still stuck at the command line, I eventually used envy to get it to so I could get back into kde. From there, I only added a couple lines to the xorg.conf that weren't put there from tutorials or scripts. for example, the only things in the modules section was originally Load "glx" and Load "extmod", and I added the others lines from other forums.

Everything works in the nvidia-settings, except for the opengl/glx tab, where it says something like "fail to query the glx module"
I am sure I installed various things for the old card, including drivers, like the r128, but the problem is it was so long ago that I don't know which tutorials I followed. I have tried uninstalling different things since I put in the nvidia card though, like libgl-mesa-dri, because forums made it sound like there isn't supposed to be any kind of dri on nvidia cards. I also uninstalled another xserver package that was specific to the r128 driver. (xserver-xorg-video-ati i think). I don't really know what might be installed that is for ati cards only, and my only guess is that the problem has something to do with something left over. I am still new to linux though, so I don't really know.

---

### Post by rwilson04 on 2007-12-28
it seems to be working now. one forum i read said that it needed the xorg sdk to build the glx module, or something, so i download some xorg packages with '-dev' in them. i don't know if that is what helped, but i downloaded the nvidia driver from their website, and ran the installation script, and it worked the next time i started x.

---

