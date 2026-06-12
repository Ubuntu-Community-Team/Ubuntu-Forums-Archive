---
title: "Beryl/XGL/ATI simple question"
date: 2006-12-08
forum: Desktop Environments
---

### Post by dschmier on 2006-12-08
I installed Beryl/XGL on a clean Edgy install according the guide at [http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/XGL]("http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/XGL")

I can log in to an XGL session just fine but when I try to start beryl-manager I get the error

```
XGL Absent, checking for NVIDIA
Nvidia Absent, assuming AIGLX
beryl: No composite extension
```

Just googling, I've found that a lot of other people have this same problem but I have yet to find a solution.  Because it seems like this is a fairly common problem, maybe someone here knows the solution.  My card is an ATI X300 and fglrx seems to be all properly installed.  fglrxinfo returns 

```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X300/X550 Series Generic
OpenGL version string: 2.0.6174 (8.31.5)
```

My XGL startup script is 

```
#!/bin/sh
Xgl :0 -fullscreen -ac -br -accel glx:pbuffer -accel xv:pbuffer &
sleep 4  
export DISPLAY=:0 
exec gnome-session

```

I could give the entire contents of my xorg.conf, but I have inserted the lines 

```
Section "Extensions"
	Option	    "Composite" "Disable"
EndSection

```

at the end of it.  

Any help would be greatly appreciated.

---

### Post by RAOF on 2006-12-08
That startup script can't work.  The reason being, you're trying to run XGL on display :0 - that's already taken by the X server already started!

You'll notice that in the HOWTO you linked to, they used **Xgl :1 *otherstuff***.  Change your startup script to match theirs.

---

