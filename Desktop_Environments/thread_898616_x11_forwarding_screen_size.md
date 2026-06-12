---
title: "x11 forwarding screen size"
date: 2008-08-23
forum: Desktop Environments
---

### Post by eok20 on 2008-08-23
Hi, I'm connecting to Ubuntu with my macbook with x11 tunneling enabled.  When I run gnome-session it seems to be using the screen size of the monitor on the Ubuntu box, which is too big.  All I am able to see is part of the desktop background and nothing else.  How can I adjust the screen size?  I thought messing around with xrandr may help but when I run it I get the error message. 

'Xlib:  extension "RANDR" missing on display "localhost:10.0".
RandR extension missing'

Thanks!

---

### Post by jpkotta on 2008-08-23
I'll bet there's a way to do it with X11 forwarding, but I know how to do it with VNC.  With x11vnc, use the -scale option.
```
x11vnc -display :0 -scale 4/5
```

---

### Post by starfall on 2009-01-15
I'm having exactly the same issue. 

I wanna connect to ubuntu 8.10 on a PC from my 10.5.6 macbook pro. The ssh connection works fine, but every time I start a GUI application using x11 forwarding, it keep saying: Xlib:  extension "RANDR" missing on display "localhost:10.0".

I've tried googling a lot, but found no solution for this. The GUI application worked with no problem, but the error message was annoying and since I'm pretty new to the linux world, I'm afraid it would cause some other errors.

Any help would be really appreciated. Thanks!

---

### Post by wyatt23 on 2009-01-19
i also have the same problem and no amount of googling has helped.

---

### Post by krunge on 2009-01-19
> **starfall said:**
> The ssh connection works fine, but every time I start a GUI application using x11 forwarding, it keep saying: Xlib:  extension "RANDR" missing on display "localhost:10.0".

I've tried googling a lot, but found no solution for this. The GUI application worked with no problem, but the error message was annoying and since I'm pretty new to the linux world, I'm afraid it would cause some other errors.


From my experience that RANDR message is harmless.  I just ignore them and have never seen anything bad come of it.

RANDR is an X server extension to allow apps to dynamically resize the screen (i.e. different resolution WxH.)  A particular app **may** want to use RANDR to go into "fullscreen" mode or something like that. So unless your app/wm **needs** to do that to function at all, the problem you are seeing is likely something else.

What is probably happening is the app is checking for the existence of the RANDR extension on the current display, and the library Xlib prints out that informational message straight to stderr.

---

### Post by Blu3fish on 2009-04-18
Had this same error, haven't quite resolved it yet - I can now get a new desktop xwindow session on my mbp (10.5.6) but isn't 100% working.

Did the following on my Ubu 8.10 box:
$ sudo apt-get install xserver-xephyr xfwm4 xfce4-session
$ Xephyr -ac -screen 1280x1024 -br -reset -terminate 2> /dev/null :2 &
$ xfce4-session

then on mbp:
$ ssh -XfC -c blowfish user@host xfce4-session

I'll keep at it.

---

