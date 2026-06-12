---
title: "xgl/compiz, dualhead lcd/tv, no desktop on second display."
date: 2006-06-27
forum: Desktop Environments
---

### Post by madscience on 2006-06-27
I'm running a dualhead setup on my laptop, using the laptop LCD and a TV on the s-video out.  I am NOT using xinerama.  It works fine using normal x and metacity, but when using xgl and compiz, the TV is only showing the default X screen (no windows, background, etc).  What I want to know, is there a way to configure the second display to show either a) another xgl enabled gnome session, or b) a second session with another window manager?
Would the following code in gdm.conf-custom enable a second xgl display:
[servers]

# Override displays to use Xgl.
0=Xgl0
1=Xgl1

[server-Xgl0]
name=Xgl0 server
command=/usr/local/bin/Xgl :0 -fullscreen -ac -accel xv -accel glx:pbuffer
flexible=true

[server-Xgl1]
name=Xgl1 server
command=/usr/local/bin/Xgl :1 -fullscreen -ac -accel xv -accel glx:pbuffer
flexible=true

or am I way off on this?

I will enable xinerama and install the debs from the quinn repo if necessary, but if there is an alternative to installing 3rd party packages, I'd rather do that first.

Thanks in advance.

---

