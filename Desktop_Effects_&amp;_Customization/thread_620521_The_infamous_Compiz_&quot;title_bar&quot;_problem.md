---
title: "The infamous Compiz &quot;title bar&quot; problem"
date: 2007-11-22
forum: Desktop Effects &amp; Customization
---

### Post by Déjà Vu on 2007-11-22
OK, so I've read each and every forum topic and wiki page about this problem, but I haven't been able to fix it.

So here's my question: **has anyone been able to fix this for good, without turning Compiz off completely?**

I'm using gtk-window-decorator, and I even put that in Compiz's "window decorator" configuration.

Below is my xorg.conf, so you can see I've tried everything.

```

Section "Module"
    Load           "glx"
    Load           "extmod"
EndSection

Section "Device"
    Identifier     "nVidia Corporation G70 [GeForce 7600 GT]"
    Driver         "nvidia"
    Option         "AddARGBVisuals" "True"
    Option         "AddARGBGLXVisuals" "True"
    Option         "NoLogo" "True"
    Option         "RenderAccel" "True"
    Option         "AllowGLXWithComposite" "True"
    Option         "DisableGLXRootClipping" "True"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation G70 [GeForce 7600 GT]"
    Monitor        "SyncMaster"
    DefaultDepth    24
    Option         "AddARGBVisuals" "True"
    Option         "AddARGBGLXVisuals" "True"
    Option         "NoLogo" "True"
    Option         "RenderAccel" "True"
    Option         "AllowGLXWithComposite" "True"
    Option         "DisableGLXRootClipping" "True"
    SubSection     "Display"
        Depth       24
        Modes      "1680x1680" "1680x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

```

Oh, and here are the driver details:

```

OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce 7600 GT/PCI/SSE2
OpenGL version string: 2.1.1 NVIDIA 100.14.19

```

---

### Post by FuturePilot on 2007-11-22
I would try removing this
```
Option         "AddARGBVisuals" "True"
    Option         "AddARGBGLXVisuals" "True"
    Option         "NoLogo" "True"
    Option         "RenderAccel" "True"
    Option         "AllowGLXWithComposite" "True"
    Option         "DisableGLXRootClipping" "True"
```
From your "Screen" section because it's already in your "device" section.
Also remove this line too from the "device" section.

Option         "DisableGLXRootClipping" "True"

Log out and log back in.

---

### Post by Déjà Vu on 2007-11-23
Sorry, but it still doesn't work...

---

### Post by Motorhead Kaze on 2007-11-29
Oh please great Compiz wizards hear our plea!

I installed Compiz from [http://phorolinux.com/how-to-install-compiz-fusion-060-from-sources-on-ubuntu-710-gutsy-gibbon.html](http://phorolinux.com/how-to-install-compiz-fusion-060-from-sources-on-ubuntu-710-gutsy-gibbon.html)  Did NOT install Emerald, 
fixed my Nvidia Xorg Conf b.s. as you did, and got the Fusion Icon Button:
git-clone git://anongit.opencompositing.org/users/crdlb/fusion-icon
cd fusion-icon
sudo make install
(so I could get Metacity back easily when everything went to pot)

and I had the cube and the title bars and then.... turned on Firefox, the window was too high, switched Compiz to Metacity, pulled the window down back to the normal location on my screen, switched Compiz back ON and poof...no title bars again.  Like mom said, "Don't play with the switch, you're gonna break it!"  I did.

So, like you, I went through many threads, and saw the one that fixed my title bars.  On this current trip with Compiz I had missed one step.  Preferences/Appearance/visual effects and clicked normal.  I did a little test with that.  I was using Metacity when I clicked that.  The title bars in Metacity went out, I switched to Compiz and now everything is working.  I tried it with the last option there "Extra" and it was no good.

Now I have no idea why everything worked for a minute without turning on visual effects, nor why none of this works at all when I get Compiz out of the Repos....but anyway, DID YOU TURN ON VISUAL EFFECTS?

I think Compiz is a buggy program.  I just wanted to make it work because I'm stubborn.

---

### Post by Znort_Ubern00b on 2007-11-29
sudo nvidia-xconfig --add-argb-glx-visuals -d 24
  type that into terminal..it worked for me in feisty

---

