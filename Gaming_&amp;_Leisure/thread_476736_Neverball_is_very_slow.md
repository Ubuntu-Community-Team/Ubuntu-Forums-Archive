---
title: "Neverball is very slow"
date: 2007-06-17
forum: Gaming &amp; Leisure
---

### Post by afflusso on 2007-06-17
I just installed ubuntu a few days ago.  I installed neverball and neverputt, and when I play them they are extremely slow and unplayable (even when the resolution is set to the lowest and shadows etc. turned off).

Armagetron works and after some tweaking 3D chess is working.  Here are my system specs:
ubuntu/XP dual boot
512mb ram
intel pentium 4
video card is nvidia tnt 400 or something, I think 32 mb.  I'm not sure about this but I could boot into XP to find out as I'm not sure how to do it in ubuntu.

In windows, I would certainly be able to run neverball at full speed even with shadows/high res. I can play unreal GOTY in XP at full speed at high res, so it must just be an issue of drivers or something. If I am leaving out any details ask me to post them.

---

### Post by cogadh on 2007-06-17
Have you installed the nVidia 3D accellerated drivers?

---

### Post by afflusso on 2007-06-17
> **cogadh said:**
> Have you installed the nVidia 3D accellerated drivers?

no. I'll restart now and see if it works.

---

### Post by cogadh on 2007-06-17
Use the instructions [here]("http://www.albertomilone.com/latest_nvidia_udsf_feisty.html"), they worked best for me. You will need to confirm exactly what video card you have before installing the driver.

---

### Post by afflusso on 2007-06-17
Thanks cogadh, I restarted and neverball works perfectly (although the controls are annoying) but the screen res is too small and I can't change it. I'll take a look at that site to find the right one.

---

### Post by afflusso on 2007-06-17
following the walkthrough, it said to type ** sudo nvidia-xconfig --no-composite** but I get an error: unrecognized option: "--no-composite"

Can I skip this step or am I typing it wrong?

---

### Post by cogadh on 2007-06-17
Did you end up using the legacy driver?

---

### Post by afflusso on 2007-06-17
Yes, it was at the end of the list

---

### Post by cogadh on 2007-06-17
In that case, skip that step but make sure you do what it says in step 7 of the "Problems" section.

---

### Post by afflusso on 2007-06-17
Before I did anything on that walkthrough, Neverball was working.  I did go up to step 7 in problems  until it said "If those options do not work" and I realized the only problem I'm having right now is my screen resolution.  It is 800x600 which needs to be fixed back to 1280x900 like before when Neverball wasn't working.  

Why would I not be able to fix the resolution to be higher?

---

### Post by cogadh on 2007-06-17
Pressing "CTRL ALT +" or "CTR ALT -" will allow you to scroll through your available resolutions.

---

### Post by afflusso on 2007-06-17
There are only two available, and the other one is worse than this one! I know it is capable of being at a higher res, as that was the case before I enabled the hardware acceleration and Neverball started working. Can I not have both at the same time?

---

### Post by cogadh on 2007-06-17
Yes you can have your cake and eat it too. :)

You need to check your xorg.conf file, it sounds like the driver install may have modified some of the settings negatively. Go to the /etc/X11 directory and open the xorg.conf file. Copy the info from the "Monitor", "Device" and "Screen" sections into a reply here so I can see what it did. When you paste the info, make sure to wrap it in CODE tags, that will preserve the layout of the copied info.

---

### Post by afflusso on 2007-06-17
```

Section "Device"
        Identifier      "nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64$
        Driver          "nvidia"
        Busid           "PCI:1:0:0"
        Option          "NoLogo"        "True"
        Option          "AllowGLXWithComposite" "True"
EndSection

Section "Monitor"
        Identifier      "CPD-G220R"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64$
        Monitor         "CPD-G220R"
        Defaultdepth    24
        Option          "ExactModeTimingsDVI" "TRUE"
        Option          "ModeValidation" "DFP-0: NoEdidDFPMaxSizeCheck, NoVesaM$
        SubSection "Display"
                Depth   1
                Modes           "1280x1024"     "1280x960"      "1152x864"     $
        EndSubSection
        SubSection "Display"
                Depth   4
                Modes           "1280x1024"     "1280x960"      "1152x864"     $
        EndSubSection
        SubSection "Display"
                Depth   8
                Modes           "1280x1024"     "1280x960"      "1152x864"     $
        EndSubSection
        SubSection "Display"
                Depth   15
                Modes           "1280x1024"     "1280x960"      "1152x864"     $
        EndSubSection 
```

---

### Post by cogadh on 2007-06-17
Ah, you appear to have a Sony 17" monitor. You are going to need to add refresh/sync rates for that monitor.

Open a terminal and enter this to make a backup of your xorg.conf:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg_backup.conf
```
Then, you will need to open the xorg.conf file for editing:
```
sudo gedit /etc/X11/xorg.conf
```
Add this to the "Monitor" section:
```
HorizSync       30-80
VertRefresh     48-170
```
Save the file, then logout and press CTRL-ALT-BACKSPACE to restart the X server. It should immediately restart at the highest resolution you have set and you can log back in.

---

### Post by afflusso on 2007-06-17
Working! thanks!

Also, ever since I installed (and on the Live CD too) the screen is not quite stretching to the edge. There are about 10-15 black pixels on a border on the left and right, and about 5 on top, and 10 on bottom.  Is there a way to make ubuntu fit, or is it a monitor setting?  I was hesitant to mess with the monitor because it would probably affect the XP look also.

---

### Post by cogadh on 2007-06-17
That's a monitor setting and yes, it will afftect XP, if you run XP at the same resolution as Ubuntu (same thing happens to me).

---

