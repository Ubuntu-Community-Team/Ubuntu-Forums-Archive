---
title: "Twinview Only One Screen?"
date: 2007-10-22
forum: Desktop Environments
---

### Post by willguy on 2007-10-22
I upgraded to gutsy recently and love it. My problem is that i am running twinview, but when i go to Screens and graphics there is only one screen with resolution that spans across both screens. This causes tons of other problems, games dont run right, cannot select primary monitor. How do i add another screen so i can customize each? Windows has done this sense 98 so i'm it cant be that hard.

---

### Post by unf on 2007-10-22
> **willguy said:**
> I upgraded to gutsy recently and love it. My problem is that i am running twinview, but when i go to Screens and graphics there is only one screen with resolution that spans across both screens. This causes tons of other problems, games dont run right, cannot select primary monitor. How do i add another screen so i can customize each? Windows has done this sense 98 so i'm it cant be that hard.

Disable XGL/Reinstall. But it is not really a solution if you wan't to use  Compiz.

---

### Post by bondik on 2007-10-22
Try playing with the /etc/X11/xorg.conf and twinview settings. See my xorg.conf I posted when I described my problem (My twinview conf works with notebook LCD and external one)  [http://ubuntuforums.org/showthread.php?p=3602669#post3602669](http://ubuntuforums.org/showthread.php?p=3602669#post3602669). Also see [http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/README/index.html]("http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/README/index.html")
for twinview parameters. (Hope you have nvidia card).

---

### Post by unf on 2007-10-22
> **bondik said:**
> Try playing with the /etc/X11/xorg.conf and twinview settings. See my xorg.conf I posted when I described my problem (My twinview conf works with notebook LCD and external one)  [http://ubuntuforums.org/showthread.php?p=3602669#post3602669](http://ubuntuforums.org/showthread.php?p=3602669#post3602669). Also see [http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/README/index.html]("http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/README/index.html")
for twinview parameters. (Hope you have nvidia card).

With XGL it dosen't

---

### Post by judolars on 2007-10-24
I have a laptop with an nVidia (Quadro NVS 135M) card, and also found that the "Screens and Graphics" tool was useless to configure a dual-monitor setup.

I have a 1440x900 LCD on my laptop and an external 1680x1050 monitor connected,and I am using the nvidia-glx-new driver since the card is fairly new. To set up TwinView, I simply added the following lines to the "Device" section in my /etc/X11/xorg.conf:

```

Option      "TwinView"
Option      "MetaModes"             "1440x900,1680x1050; 1440x900,NULL"
Option      "TwinViewOrientation"   "LeftOf"

```

It works perfectly, and even selects the second MetaMode -- the one where only the laptop LCD is enabled -- automatically whenever the second monitor is not connected.

Make sure Xinerama is not enabled.

---

### Post by judolars on 2007-10-24
...or did I misunderstand your question? Perhaps you already have TwinView up and running, but still have problems? The point with TwinView, as I understand it, is that there are no "primary" and "secondary" monitors. It works with the nVidia driver to hide the dual-monitor setup completely from X, so all X sees is one single (huge) screen. If you have problems running games and such, I believe it is recommended to switch to a single monitor when playing. Just add the required "MetaMode" to the setup above.

See also: [http://ubuntuforums.org/showthread.php?t=221174]("http://ubuntuforums.org/showthread.php?t=221174")

---

### Post by madhakish on 2007-10-31
This used to be accomplished by enabling the Xinerama extension however I believe that the "metamodes", "ConnectedMonitor", and "TwinViewOrientation" options do the same thing when defined properly.

I have what I believe you are looking for functionality-wise, that is I have 2 screens inside a "virtual screen" of 2880x900, each one is 1440x900, each is identified independently and see as separate screens by KDE (Gnome does not have good support for this functionality). When KDM starts the login box is centered on the "right" screen, when new applications open they open based off which screen they were last "in" or the screen the panel that launched them resides on. I have separate panels on each screen and borders are recognized properly IE windows lock to a border, don't open centered between the two etc.

If this is what your looking for, perhaps the following "Screen" section of my config can be of some help. I used to run 3 heads this way and it worked just as well. IMHO KDE is FAR superior to Gnome when it comes to dealing with multiple heads.. My systems works exactly the way I envisioned it would running dual-monitors. This also gives me proper multi-head Compiz support although there's as long ways to go for Compiz + KDE - if KDE does better with dual-head, Gnome does better with Compiz.

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewOrientation" "DFP-0 LeftOf CRT-0"
        #Option         "UseEdidFreqs" "True" 
    Option         "metamodes" "CRT-0: 1440x900_75 +1440+0, DFP-0: 1440x900_75 +0+0"
    Option         "RenderAccel" "1"
    Option         "AllowGLXWithComposite" "true"
    Option         "ConnectedMonitor" "DFP-0,CRT-0"
    Option         "coolbits" "1"
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       24
        Modes      "1440x900@75"
    EndSubSection
EndSection


Good luck!

---

