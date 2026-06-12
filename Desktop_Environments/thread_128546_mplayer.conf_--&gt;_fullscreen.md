---
title: "mplayer.conf --&gt; fullscreen"
date: 2006-02-11
forum: Desktop Environments
---

### Post by nalmeth on 2006-02-11
I read on another post that creating a mplayer.conf file in your ~/.mplayer folder lets you tell mplayer exactly what you want it to do, in this case, make the video go completely fullscreen. I created this file in ~/.mplayer, as I have no /usr/local/etc folder. 


mplayer.conf:
```
##
## MPlayer config file
##
## This file can be copied to /usr/local/etc/mplayer.conf and/or ~/.mplayer/config .
## If both exist, the ~/.mplayer/config's settings override the
## /usr/local/etc/mplayer.conf ones. And, of course command line overrides all.
## The options are the same as in the command line, but they can be specified
## more flexibly here. See below.
##

vo=xv # To specify default video driver (see -vo help for
# list)
ao=oss # To specify default audio driver (see -ao help for
# list)

fs=yes # Enlarges movie window to your desktop's size.
# Used by drivers: all

vm=yes # Tries to change to a different videomode
# Used by drivers: dga2, x11, sdl

bpp=24 # Force changing display depth.
# Valid settings are: 0, 15, 16, 24, 32
# may need 'vm=yes' too.
# Used by drivers: fbdev, dga2, svga, vesa

zoom=yes # Enable software scaling (powerful CPU needed)
# Used by drivers: svga, x11, vesa

#double=yes # use double-buffering (recommended for xv with
# SUB/OSD usage)

# monitoraspect=4:3 # standard monitor size, with square pixels
# monitoraspect=16:9 # use this for widescreen monitor! non-square pixels

##
## Use GUI mode by default
##

gui = yes
```

"fs=yes # Enlarges movie window to your desktop's size.
# Used by drivers: all"

This is the option I'm looking for. Only this doesn't change anything. Mplayer works like normal, and no actual fullscreen. Still black border, and small video.

---

### Post by taurus on 2006-02-11
Look in ~/.mplayer where you should have a file called gui.conf.  In there, there is an option

load_fullscreen = "yes"

---

### Post by nalmeth on 2006-02-11
That makes mplayer load up in fullscreen, but still the actual video does not expand to the entire desktop space.

---

### Post by taurus on 2006-02-11
What vo_driver are you using???  Play around with different drivers until you get the one that displays fullscreen...

---

### Post by nalmeth on 2006-02-11
the gui.conf files says I'm using the x11 driver. What should I change this to?

---

### Post by taurus on 2006-02-11
Try the xv driver...

---

### Post by jsiii on 2006-02-12
[QUOTE=nalmeth]That makes mplayer load up in fullscreen, but still the actual video does not expand to the entire desktop space.[/QUOTE]

I tried the config above, but Mplayer kept crashing. I solved it by using OpenGL video driver (in Mplayer preferences, tab Video)

---

### Post by bruno.vitorino on 2006-03-01
[QUOTE=jsiii]I tried the config above, but Mplayer kept crashing. I solved it by using OpenGL video driver (in Mplayer preferences, tab Video)[/QUOTE]
The OpenGl driver works for me :)

---

### Post by jazzi on 2006-03-05
[SIZE="4"]that's the solution:
edit the file:  > sudo gedit /etc/mplayer/input.conf
and add the following lines into it 
> f    vo_fullscreen
Then when you click the f your mplayer will be fullscreen,also you can change the f to anyothers[/SIZE]

---

### Post by tommywong128 on 2007-12-31
I also try to change the config file and the same.  Lateron I goto preference and under Video Tab, I try  xv X11/Xv (available driver) and its working good now. The screen in the middle can change size.  

Please check if it can work on yours one.

Good Luck

---

