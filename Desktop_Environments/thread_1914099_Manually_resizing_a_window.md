---
title: "Manually resizing a window"
date: 2012-01-23
forum: Desktop Environments
---

### Post by freakalad on 2012-01-23
I have a host that's running *only* X, with no Desktop Environment (DE) or Window Manager (WM). It's only a ultra-skinny X box, to support a lean media centre.

I basically `xinit` XBMC to start at boot (via a combination of startup configs/scripts), and I've created a simple bash script that I invoke from within XBMC to run GMPC as my MPD client. 
It starts up fine, but only occupies about quater of my screen, and I can resize it using my mouse, but I'm having a *lot* of difficulty to resize the window using any other means.

I've looked at [wmctl]("http://www.linuxjournal.com/magazine/hack-and-automate-your-desktop-wmctrl"), but since there's not WM, that's a bust.

I've tried using the ["-geometry" argument provided by Xorg]("http://www.x.org/archive/X11R6.8.1/doc/X.7.html"), but the CLI's stdout returns:
```
** ERROR **: Failed to parse commandline options: Unknown option -geometry
```

I've tried to make use of *xdotool* & *xwit*, but it doesn't seem to have any effect. (although this seems the right way to go about this)
Could be that I'm using the wrong syntax, but I'm not getting any errors

Does anyone have any insight info how I can grab, focus & resize/maximize a particular (arbitrary/GTK) window using only the CLI, with no intervention from input devices, such as a keyboard or mouse?

---

### Post by freakalad on 2012-01-23
OK - I think I might have a solution (although admittedly not an ideal one)

I've *HAD* to install a window-manager - settled on [Awesome]("http://awesome.naquadah.org/") , since it seems very lightweight & responsive.

I've now modified the startup script to look look this:
```

#!/bin/bash

#execute GMPC
/usr/bin/gmpc --fullscreen >> /tmp/mpd.client.log

#when GMPC exits, find, focus & bring to the front a window named "XBMC" 
wmctrl -r XBMC -b fullscreen,above
wmctrl -R XBMC 

#XBMC presents in a non-fullscreen more; send the "\" keystroke to maximize it 
xdotool key backslash

exit 0

```

I hope this is useful to someone :)

---

