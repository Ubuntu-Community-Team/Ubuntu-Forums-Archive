---
title: "Nvidia + KDE = Tearing"
date: 2010-05-26
forum: Desktop Environments
---

### Post by XAZero on 2010-05-26
Hi all 

Ive been experiencing tearing (whole screen not only xv), when composite is enabled and the nvidia drivers installed, even if i have vsync turned on .


also i have to say that _if i enable the snow effect the tearing completely disappears and the fps plugin says kwin is running exactly at 61 fps (which is the right value)_ but if i turn of the snow effect the tearing eventually comes back.
that makes me think that only opengl apps are getting the vsync. (and the snow effect makes the whole desktop to be opengl drawn i guess).

also see

[http://forum.kde.org/viewtopic.php?f=15&t=88200](http://forum.kde.org/viewtopic.php?f=15&t=88200)
[http://www.nvnews.net/vbulletin/showthread.php?p=2261238#post2261238](http://www.nvnews.net/vbulletin/showthread.php?p=2261238#post2261238)

HW:macbook pro 5,5
-GPU: nvidia geforce 9400m

SW: Kubuntu 10.04
-nvidia drivers: 195.36.15
-Xorg(server vendor version): 1.7.6
-KDE SC: 4.4.3
-QT:4.6.dontknow

Config:

-xorg.conf
> ...
Option "NoLogo" "True"
_Option "TripleBuffer" "True"_
Option "DynamicTwinView" "False"
Option "BackingStore" "True"
Option "RenderAccel" "True"
Option "DamageEvents" "True"
Option "PixmapCacheSize" "1024000"
Option "AddARGBGLXVisuals" "True"
Option "AllowIndirectPixmaps" "True"
...
Driver "nvidia"
...

-~/.xinitrc
> _export __GL_SYNC_TO_VBLANK=1_
#export QT_GRAPHICSSYSTEM=opengl ##I KNOW IT DOESN'T WORK BUT I WISH IT DID
nvidia-settings --load-config-only
nvidia-settings -a InitialPixmapPlacement=2 -a GlyphCache=1
. /etc/X11/xinit/xinitrc

kwinrc
Quote:
> [Compositing]
AnimationSpeed=2
Backend=OpenGL
CheckIsSafe=true
DisableChecks=true
Enabled=true
GLDirect=true
GLMode=TFP
GLTextureFilter=2
_GLVSync=true_
HiddenPreviews=6
_RefreshRate=60_
UnredirectFullscreen=true
#XRenderSmoothScale=true
...

.nvidia-settings-rc
> ...
_0/SyncToVBlank=1_
...
0/OpenGLImageSettings=1 # dont know what's this for
...
0/XVideoTextureSyncToVBlank=1
...

---

### Post by Diego318 on 2010-09-23
Any updates to this?

---

### Post by XAZero on 2010-09-23
> **Diego318 said:**
> Any updates to this?

Hi Diego

I'm testing Kubuntu 10.10 and it seems that the problem is fixed now.
I suppose it is related to qt 4.7 or to the new Nvidia driver (or to both).

But I still need to disable TwinView so the right refresh rate gets exported to Kwin (among other things).

I'll post a guide after the release.

Kind regards.

---

### Post by xrhstaras on 2011-07-18
SAME HERE! I have nvidia 9400M and found big troubles !
Excessive tearing on xubuntu and kubuntu
when i try to play 1080p mkv via vlc 
Flash video on youtube or other sites also has Tearing.

The only thing i managed to make is on ubuntu 64bit 11.04 to have perfect 1080p video playback with vlc but flash video is the same, has tearing. (tried the 11 version of flash, same or worst!)

Lets admit it something isn't right and i dont know what it is, maybe its the driver/module maybe the configuration i dont know , i know that on my machine linux sucks after all.

PS1:  On windows 7 1080p video playback and flash video playback is 100% perfect.

---

### Post by jawilljr on 2011-07-18
Turn off compositing.  You can't have both.

Jerry

---

