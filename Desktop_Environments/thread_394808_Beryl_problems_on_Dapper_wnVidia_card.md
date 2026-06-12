---
title: "Beryl problems on Dapper w/nVidia card"
date: 2007-03-27
forum: Desktop Environments
---

### Post by Screaming Monkey on 2007-03-27
Hey there.  I've been fiddling around with getting Beryl to work on my Dapper box and have run into a bit of a snag... 

I went through the install process using this guide [http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Dapper_with_XGL]("http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Dapper_with_XGL")
and all seemed to go ok until I logged out and when I logged into the Xgl session (I created a separate session) it hung there for about 30 or so seconds then kicked me back to the login screen.

I then went to the troubleshooting section on the Beryl Wiki site, found this: []("http://wiki.beryl-project.org/wiki/Troubleshooting_Beryl#Gnome_splash_hangs_when_using_Beryl") and attempted to ratify the problem.  My xserver hung and I restarted it.  I then checked my glxinfo | grep direct and got this:

> Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".


And now I am stuck on what to do next.  Anyone willing to help a semi-newb out?  Thanks! (If you want me to post any of my specs, just let me know what to type into a terminal to get it...like I said, still newb!)

---

