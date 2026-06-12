---
title: "Using different video drivers for different programs"
date: 2007-09-23
forum: Desktop Environments
---

### Post by WastedMeat on 2007-09-23
The proprietary ATI drivers suck with my Radeon Xpress 200m.  The x server will frequently freeze when a session is starting or ending, and there is much more tearing when windows move.  The xserver occasionally hangs for twenty seconds or so if the computer is under load, and none of this happens with the open driver.

I want to run the open source driver, and run the programs that need opengl in a distinct x-session using the proprietary driver, by launching them with something like 

xinit --config /etc/X11/xorg.conf.fglrx $1 -- :1

but the documentation for xinit and startx does not appear to mention an option for specifying a configuration file.  I could define two different devices in my xorg.conf, and specify the device on the command line, but I am unsure of the syntax for this.

Additionally, Ubuntu likes to tell me that I am not authorized to run the X-server if I try to launch one from within an active session (specifying a different display).  If I switch to a text VT while an x-session is running, there are no problems starting a second session.  Assuming there is a way to do make this hardware work like this, its utility would be very much damaged if I could not embed the call in the applications menu.

I am also unsure if this will work on an ATI card.  I know the nVidia hardware in my desktop can handle running two simultaneous sessions with different drivers (I do not remember the occasion, but I was manually modifying the config file between sessions), but my nVidia card can do lots of things that this ATI POS cannot.

I do know that my card and/or ATI linux drivers in general cannot support OpenGL on multiple virtual displays. That is not what I am trying to do.

---

