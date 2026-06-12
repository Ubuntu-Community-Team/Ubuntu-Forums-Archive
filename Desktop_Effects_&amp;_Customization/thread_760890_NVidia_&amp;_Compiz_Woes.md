---
title: "NVidia &amp; Compiz Woes"
date: 2008-04-20
forum: Desktop Effects &amp; Customization
---

### Post by JLucien on 2008-04-20
I have a Asus NVidia EN 8800GT graphics card on my clean Gutsy system that cannot enable desktop effects from System->Preferences->Appearance.

When I type "compiz" into a terminal window I get the following output:

```
Checking for Xgl: not present. 
No whitelisted driver found
SKIP_CHECKS is yes, so continuing despite problems.
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1680x1050) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
/usr/bin/compiz.real (core) - Fatal: No GLXFBConfig for default depth, this isn't going to work.
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0

```

The output of "lspci | grep VGA" is:

```
01:00.0 VGA compatible controller: nVidia Corporation Unknown device 0611 (rev a2)
```

So it seems I don't have the proper nVidia driver, but other than this my graphics are great.

My xorg.conf is as follows:

```
Section "Files"
EndSection

Section "Device"
        Identifier      "Generic Video Card"
        Driver          "vesa"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       30-70
        VertRefresh     50-160
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Generic Video Card"
        Monitor         "Generic Monitor"
        DefaultDepth    24
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
EndSection

```

These are just the relevant parts.  I have read through a lot of the posts with similar problems but I cannot determine what I should do here.  I installed the "nvidia-glx-new" package but got a system hang, so I uninstalled it again.  I know my card is powerful enough for this, I just cannot get it to work.

Can anyone help me help myself?

---

### Post by sdennie on 2008-04-20
You may want to try to install the latest nvidia drivers using the envy program: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

I'm not sure how good the support for 8 series cards is on 7.10 (which would explain why it hangs and you are using the vesa driver).

---

### Post by JLucien on 2008-04-21
The Envy program, combined with a forum search of "compiz cube" turned up [this article]("http://ubuntuforums.org/showthread.php?t=759252&highlight=compiz+cube") gave me everything I needed.

Thanks so much!!

---

