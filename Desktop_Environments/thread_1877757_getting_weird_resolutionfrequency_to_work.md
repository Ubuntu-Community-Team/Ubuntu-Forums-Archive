---
title: "getting weird resolution/frequency to work"
date: 2011-11-08
forum: Desktop Environments
---

### Post by speakup on 2011-11-08
Hi,

I have problems getting the native resolution 960x540 to work on my Sharp Aquos LC-26p50e when connecting an Acer Revo 3600 with Nvidia Ion display adapter via HDMI with Ubuntu 11.10 (Oneiric) 32bit installed.

I've done quite a bit of research but after battling with it for 4 evenings in a row, I thought I turn to the experts on this list. :-).

What I've done so far is the following:

As the weird native resolution isn't listed in either nvidia settings or display settings in GUI, I tried to tweak the /etc/X11/xorg.conf file.

When I add the line below to the Screen section of xorg.conf then it defaults back to 720x576 which crops lots image off the screen (overscan I believe this is called)

```
Option "metamodes" "960x540 +0+0"
```
Then I read ([http://forum.xbmc.org/showthread.php?t=54685](http://forum.xbmc.org/showthread.php?t=54685))  that I can get X-server to read all modes/resolutions my TV would be able to handle and from there build a Modeline I could use in xorg config. So I ran the command below (after stopping lightdm)
```
X -verbose 6 > xlog.txt 2>&1
```This showed me the following:
```
(**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID has been
(**) NVIDIA(0):     enabled on all display devices.
(II) NVIDIA(0): Frequency information for SHARP HDMI (DFP-1):
(II) NVIDIA(0):   HorizSync   : 15.000-46.000 kHz
(II) NVIDIA(0):   VertRefresh : 49.000-61.000 Hz
(II) NVIDIA(0):     (HorizSync from EDID)
(II) NVIDIA(0):     (VertRefresh from EDID)
----
(II) NVIDIA(0):   Validating Mode "960x540":
(II) NVIDIA(0):     960 x 540 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 69.25 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  960,  984
(II) NVIDIA(0):       HSyncEnd, HTotal : 1000, 1040
(II) NVIDIA(0):       VRes, VSyncStart :  540,  541
(II) NVIDIA(0):       VSyncEnd, VTotal :  544,  555
(II) NVIDIA(0):       H/V Polarity     : +/-
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     HorizSync (66.6 kHz) out of range (15.000-46.000 kHz);
(II) NVIDIA(0):         however, ignoring HorizSync check for DFP frontend
(II) NVIDIA(0):         mode validation
(II) NVIDIA(0):     Mode (960 x 540) is too large for DFP Native Resolution
(II) NVIDIA(0):         (Max: 720 x 576); mode will not be allowed to scale to
(II) NVIDIA(0):         the DFP's native resolution.
(WW) NVIDIA(0):     Unable to use mode "960x540" for SHARP HDMI (DFP-1);
(WW) NVIDIA(0):         cannot compute backend DFP timings (mode is larger
(WW) NVIDIA(0):         than native backend 720 x 576).
(WW) NVIDIA(0):     Mode is rejected: Unable to determine BestFit backend DFP
(WW) NVIDIA(0):     timings.
```This doesn't seem right, so thing somewhere either the specs in my manual are wrong or for some reason Sharp failed to correctly report it's native resoluting to X.

Then I read that there are ways of overriding some checks and forcing certain resolutions. Next I added the following to the Monitor section in my xorg.conf 

```
Option      "ExactModeTimingsDVI" "TRUE"
```Running the command "X -verbose 6 > xlog.txt 2>&1" again now shows me a bit more hopeful:
```

(II) NVIDIA(0):   Validating Mode "960x540":
(II) NVIDIA(0):     960 x 540 @ 60 Hz
(II) NVIDIA(0):     Mode Source: X Server
(II) NVIDIA(0):       Pixel Clock      : 69.25 MHz
(II) NVIDIA(0):       HRes, HSyncStart :  960,  984
(II) NVIDIA(0):       HSyncEnd, HTotal : 1000, 1040
(II) NVIDIA(0):       VRes, VSyncStart :  540,  541
(II) NVIDIA(0):       VSyncEnd, VTotal :  544,  555
(II) NVIDIA(0):       H/V Polarity     : +/-
(II) NVIDIA(0):       Extra            : DoubleScan
(II) NVIDIA(0):     HorizSync (66.6 kHz) out of range (15.000-46.000 kHz);
(II) NVIDIA(0):         however, ignoring HorizSync check for DFP frontend
(II) NVIDIA(0):         mode validation
(II) NVIDIA(GPU-0):     BestFit Scaled and BestFit AspectScaled are identical;
(II) NVIDIA(GPU-0):         collapsing BestFit AspectScaled.
(II) NVIDIA(GPU-0):     BestFit Centered and BestFit Scaled are identical;
(II) NVIDIA(GPU-0):         collapsing BestFit Scaled.
(II) NVIDIA(GPU-0):     BestFit Centered         960x1080
(II) NVIDIA(GPU-0):       Horizontal Taps        1
(II) NVIDIA(GPU-0):       Vertical Taps          1
(II) NVIDIA(GPU-0):       Base SuperSample       x1
(II) NVIDIA(GPU-0):       Base Depth             32
(II) NVIDIA(GPU-0):       Distributed Rendering  1
(II) NVIDIA(GPU-0):       Overlay Depth          32
(II) NVIDIA(0):     Mode is valid.
...
(II) NVIDIA(0): "960x540"            :  960 x  540 @  60.0 Hz DoubleScan  (from: X Server)
(II) NVIDIA(0): "960x540d60"         :  960 x  540 @  60.0 Hz DoubleScan  (from: X Server)
```
I added the following go the Monitor section:

```
     Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "SHARP HDMI"
    HorizSync       15.0 - 46.0
    VertRefresh     49.0 - 61.0
    Modeline "960x540" 69.25 960 984 1000 1040 540 541 544 555 +hsync -vsync DoubleScan
    Option         "DPMS"
    Option      "ExactModeTimingsDVI" "TRUE"

```Under the Screen section in the subsection Display I added:
```
 Modes      "960x540"
```When I then start lightdm again I don't get any screen at all. Strange enough I don't see any weird errors in /var/log/Xorg.0.log.

Even enabling the following in Device section:
```
  Option "ModeValidation" "NoEdidModes"
```and disabling the following in the Monitor section
```
 #    Option         "DPMS"
```didn't make a difference. Still a black screen.

Searching a bit more I found someone successfully using the modeline below

[http://www.avforums.com/forums/lcd-led-lcd-tvs/510420-sharp-aquos-lc26p50e-modeline-xorg-conf.html](http://www.avforums.com/forums/lcd-led-lcd-tvs/510420-sharp-aquos-lc26p50e-modeline-xorg-conf.html)

```
Modeline "960x540" 37.26 960 1008 1040 1088 540 542 548 563 +hsync +vsync
```This one did at least started X and also showed something on the screen but the picture was horizontally duplicated flickering continuesly. I then started to play with the Pixel clock setting. This resulted in some progress, but when I change the pixel clock frequency in the modeline to either 30 or 36 the image is very unsteady like the frequency is set too low.

My question now is, how to best approach this issue and find the best resolution/frequency for my TV. I have actually considered buying another TV, but think I'll have a hard time convinsing my wife getting rid of this one simply because I can't get the this new toy of mine to work how I want it to.

All the best.

---

