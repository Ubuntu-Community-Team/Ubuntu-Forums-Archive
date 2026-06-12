---
title: "Quake 4 no video"
date: 2011-06-03
forum: Gaming &amp; Leisure
---

### Post by Pizarro on 2011-06-03
I have installed quake4 using the normal instruction "http://www.blog.highub.com/linux/install-and-play-quake-4-on-ubuntu/" and everything seemed to go ok.
But on running the game the screen goes blank and monitor reports out of frequency.Judging by the audio the game is running the intro. I'm sure it is as I've played it before on a previous ubuntu install when this same machine was dual booting. Video card is a geforce 7600gs. I have edited the config file to make the game in English as I remembered it defaults to Spanish. I assume I have to tweak another config to solve my problem but have no idea what.

---

### Post by Perfect Storm on 2011-06-04
'Out of Frequency' means that the game is running a resolution your computer can't handle or Xorg isn't set up for. You need to open quake 4 setting/ini file and manually set the resolution of the game.

---

### Post by Pizarro on 2011-06-04
Don't know if this helps

"Section "Monitor"

    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "FUS L19W-2SA"
    HorizSync       31.0 - 83.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7600 GS"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24

Can't seem to see quake 4 setting/ini file !

---

### Post by Perfect Storm on 2011-06-04
I don't have Quake 4 but there should be a file in your home directory which you can edit to manually editing Quake 4 settings. It's a hidden file/folder in your home directory.

---

### Post by Pizarro on 2011-06-04
There is a file called Quake4Config.cfg in a hidden .quake4 folder
is this what I'm looking for ?
seta image_filter "GL_LINEAR_MIPMAP_LINEAR"

seta r_skipSky "0"

seta r_forceAmbient "0"

seta r_debugArrowStep "120"

seta r_debugLineWidth "1"

seta r_debugLineDepthTest "0"

seta r_forceLoadImages "0"

seta r_shadows "1"

seta r_useSMP "0"

seta r_skipBump "0"

seta r_skipSpecular "0"

seta r_skipNewAmbient "0"

seta r_renderer "best"

seta r_ignoreHWGamma "0"

seta r_brightness "1.2"

seta r_gamma "1"

seta r_swapInterval "0"

seta r_useIndexBuffers "0"

seta r_customHeight "900"

seta r_customWidth "1440"

seta r_fullscreen "1"

seta r_displayRefresh "0"

seta r_mode "4"

seta r_aspectRatio "0"

seta r_alphaToCoverage "1"

seta r_multiSamples "0"

seta gui_mediumFontLimit "0.60"

seta gui_smallFontLimit "0.30"

This is the part I think may be appropriate.

Also how do I get out of the blank screen ? Ctrl Alt Backspace doesn't work
 This is part of it that I think may be appropriate

---

### Post by Pizarro on 2011-06-04
I have adjusted the file , Full screen to no and changed sizes to less than full screen. Game starts and runs in window.Have then adjusted video setting from within the game and all video is good.
 BUT the sound is so far behind the action,several seconds,that it is a very hard to play.

---

### Post by Pizarro on 2011-06-04
Sound cured by this thread
[http://ubuntuforums.org/showthread.php?t=1564210](http://ubuntuforums.org/showthread.php?t=1564210)

---

