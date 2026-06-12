---
title: "how to for openbox on two monitors"
date: 2009-10-10
forum: Desktop Environments
---

### Post by nephish on 2009-10-10
Hello all, 
I have two monitors that i can set up in gnome easy enough with an nvidia card and basic edits to the xorg.conf 
I am a fan of openbox though, and when i log into gdm and select openbox session, it only loads up one instance. 
On my computer that uses arch, i do not use gdm, just startx from the command line, and i have a .xinitrc that has
```
DISPLAY=:0.0 exec openbox-session &
DISPLAY=:0.1 exec openbox-session
```

i don't know to pull this off in ubuntu though.

thanks for any tips.

---

### Post by urukrama on 2009-10-13
I have never tried this, but this is what the [Openbox FAQ]("http://icculus.org/openbox/index.php/Help:FAQ#How_do_I_run_Openbox_across_multiple_X_screens.3F") says:

> In order to have Openbox manage multiple X screens (this is not the same as multi-monitor TwinView or Xinerama), you need to run an instance of Openbox directly on each screen. We've put work into making Openbox work well with other instances of itself, for this type of configuration. 

In order to run Openbox on two screens, use commands such as these: 
```
# run openbox on the second screen (they start from 0)
DISPLAY=:0.1 openbox
# by default openbox will run on the first screen (screen number 0)
exec openbox-session
```

---

### Post by nephish on 2009-10-13
ok, was doing something similar. Now will just put something like this in the openbox menu. 
thanks, will let you know how it works out.

---

