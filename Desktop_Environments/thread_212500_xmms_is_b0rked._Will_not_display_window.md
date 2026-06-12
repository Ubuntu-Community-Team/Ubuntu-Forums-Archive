---
title: "xmms is b0rked. Will not display window"
date: 2006-07-10
forum: Desktop Environments
---

### Post by kickaha on 2006-07-10
Hi.

I'm running 6.06, with gnome and a bunch of stuff out of automatix.

My problem seems to have started after I tried to experiment with xgl/compiz, although I'm not sure that is an issue.

At this point, when I try to run xmms, it starts, but will not display a window. It's there, and if I click ont the window in the gnome panel window list, it does some window move outline activity, but never shows a window.

I can find it in ps, and kill -9 it, but no window, no joy.

Any suggestions?

Thanks in advance,

kickaha

---

### Post by croak77 on 2006-07-10
Try starting it from a terminal and see if there are any error messages.

---

### Post by kickaha on 2006-07-10
kickaha@nnnn:~$ xmms
Message: device: hw:1,0
Gdk-ERROR **: BadMatch (invalid parameter attributes)
  serial 1488 error_code 8 request_code 72 minor_code 0
Gdk-ERROR **: BadMatch (invalid parameter attributes)
  serial 1489 error_code 8 request_code 72 minor_code 0

Thanks for your help

Additionally; I tried to back out the compiz and xgle stuff, due to some incidental bad behaviour, and gdm wouldn't start up. I re-installed xgl to get back to a graphical login.
I guess this could be part of a larger interaction between xorg and xgl, but I'm trying to trouble-shoot my media player. :)

---

