---
title: "xorg.conf tweaking pays off :)"
date: 2010-02-10
forum: Gaming &amp; Leisure
---

### Post by Eirinjas on 2010-02-10
My system is unlucky enough to have an ATI Radeon 9800 XT video card.  When I installed Ubuntu and tried running some of my favorite FPSes, I was severely disappointed.  Urban Terror, which blazes on the same system in Windows XP with settings maxed, was crawling in 16 bit color and low settings.  Upping the texture detail or color depth caused texture thrashing and other oddities.  So, I read everything I could find regarding 3D gaming in Linux and did some experimenting.  

Okay, so I'm stuck with the open source drivers, so there isn't much I can do there.  I ditched Pulseaudio - removing it completely, cuz I found it unreliable, and often the cause of framerate issues, and now only use ALSA. 

I created an xorg.conf file and, after alot of trial and error, found the options below to be of great benefit.  Games that were literally unplayable, like Nexuiz, are now running like champs.  Urban Terror was too slow and ugly to enjoy before, but now runs almost as swell as it does in Windows, and in all it's 32 bit - hi-res texture glory!  I hope the options can help others, but I'm also interested in feedback - if there are options I'd be better off using or trying.  Alien Arena is still thoroughly unplayable - literally in the single digit FPS range.  Sauerbraten runs pretty good, until you're in a large outdoor map and then it turns into molasses.  I have a 3.2 ghz dual processor machine, so running like molasses shouldn't be the case.

Section "Device"
        Identifier      "Radeon 9800"
        Driver          "radeon"
        BusID           "PCI:1:0:0"
        Option          "HWcursor" "on"
        Option          "SWcursor" "off"
        Option          "AccelMethod" "exa"
        Option          "AccelDFS" "true"
        Option          "BusType" "AGP"
        Option          "AGPMode" "8"   
        Option          "EnableDepthMoves" "on"
        Option          "FBTexPercent" "80"
        Option          "UseFastTLS" "2"
        Option          "BackingStore" "true"
        Option          "EnableAGPDMA" "true"
        Option          "FramebufferWC" "true"
        Option          "EXAOptimizeMigration" "true"
        Option          "MigrationHeuristic" "greedy"
        Option          "DRI" "on" 
        Option          "ScalerWidth" "2048"
        Option          "RenderAccel" "on"
        Option          "ColorTiling" "on"
        Option          "EnablePageFlip" "on"
        Option          "Tiling" "true"
        Option          "PageFlip" "true"
        Option          "BufferTiling" "true"
        Option          "LocalTextures" "true"
        Option          "DynamicClocks" "off"
        Option          "Legacy3D" "true"
EndSection

Section "Module"
  Load  "glx"
  Load  "dri"
  Load  "drm"
  Load  "extmod"
  Load  "GLcore"
EndSection

Section "DRI"
    Mode 0666
EndSection

Section "Extensions"
    Option "Composite" "Enable"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Radeon 9800"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes        "1024x768"
                Virtual         1024 768
        EndSubSection
EndSection

---

### Post by Melcar on 2010-02-10
Were did you get those options?  I don't remember many of them when I generated a xorg.conf file with Karmic.  One of my machines has a 9800pro with an old AthlonXP @ 2GHz and 512MB of RAM, and runs nearly all open source games with medium to low settings at 1024x768.  No tweaks on my xorg.conf either.
Some of those options are "on" be default, by the way.  Check the radeon manual ("man radeon" on a terminal) to get a listing of available options.  You can also check your Xorg.0.log to see if the options you're specifying and being used or are producing errors.  There is also the *driconf* tool that you can install; it's a GUI that allows you to easily change a few 3D related options that may or may not help in certain situations.

---

### Post by Eirinjas on 2010-02-10
Thanks for the response, Melcar.  I know the X server is supposed to autodetect alot of stuff and enable it by default, but I also understand alot of people have issues that require tinkering to fix.  The settings I added to my xorg.conf were based on research and experimentation, and it has helped in my own configuration tremendously.  I'm going through the log now.  One thing that stands out, and which I kind of knew, is that the driver is only using half of my video card's ram.  I suspect some of the issues I've had with texture thrashing and such are a result of this.  Any idea why it sees the full ram, but only decides to use half?  From my log:


(II) RADEON(0): Generation 1 PCI interface in multifunction mode, accessible memory limited to one aperture
(II) RADEON(0): Detected total video RAM=262144K, accessible=131072K (PCI BAR=131072K)
(--) RADEON(0): Mapped VideoRAM: 131072 kByte (256 bit DDR SDRAM)

---

### Post by Melcar on 2010-02-10
It's a bit complicated (I didn't understand half of what was said on a discussion relating to this), but it's basically a driver limitation.  [Here]("http://www.phoronix.com/forums/showthread.php?t=12164") is an old discussion on the subject.  Obviously the driver has progressed a lot since then, but memory management is barely going upstream.  Right now the maximum vRAM that the driver can access is 256MB, but that's further limited in some chips (particularly the older ones like yours).

---

### Post by Eirinjas on 2010-02-10
Thanks for the info.  BTW, the xlog reported the following settings as not used, so I removed them.  The rest work, and some of them are not enabled by default.

(WW) RADEON(0): Option "HWcursor" is not used
(WW) RADEON(0): Option "UseFastTLS" is not used
(WW) RADEON(0): Option "EnableAGPDMA" is not used
(WW) RADEON(0): Option "FramebufferWC" is not used
(WW) RADEON(0): Option "Tiling" is not used
(WW) RADEON(0): Option "PageFlip" is not used
(WW) RADEON(0): Option "BufferTiling" is not used
(WW) RADEON(0): Option "LocalTextures" is not used
(WW) RADEON(0): Option "DynamicClocks" is not used
(WW) RADEON(0): Option "Legacy3D" is not used

---

### Post by Eestlane on 2010-03-25
Thanks for this thread.

I have ATI 9800 Pro (R350).

glxgears initially had 600 FPS
With your x.org settings it raised to 725 FPS
If I also turned compiz off, it raised to 1000

(By the way, glxgears gives much better FPS results, if it's window is active (e.g it's titlebar is highlighted while other windows arent)

---

