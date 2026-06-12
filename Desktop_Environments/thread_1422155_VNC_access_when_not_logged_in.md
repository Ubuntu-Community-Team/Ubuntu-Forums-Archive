---
title: "VNC access when not logged in"
date: 2010-03-05
forum: Desktop Environments
---

### Post by dargaud on 2010-03-05
Hello all,
I'd like to figure out a general solution to the following problem.
I have several boxes (not all are Ubuntu, but all use KDE) that need remote access. If there's a user logged in, even if the screensaver has kicked in, VNC will work fine. But after a reboot, when all you have is the KDE user/password prompt, VNC won't work. I use x11vnc, tried with various parameters.

So how can I either VNC at this stage or get the login to go further via pure ssh and then proceed with VNC ? The problem is probably the same as [this one]("http://ohioloco.ubuntuforums.org/showthread.php?t=1314958") and related to magic X cookies, but none of the solutions I've seen seem to work.

On the client side I get a "connection closed" after the "Status: security type requested", and on the server side, I get
```
wait_for_client: running: env X11VNC_SKIP_DISPLAY=''  /bin/sh /tmp/x11vnc-find_display.DiY6VF
wait_for_client: find display cmd failed
wait_for_client: bad reply '
'
```

I should add that the [method described here]("http://www.karlrunge.com/x11vnc/faq.html#faq-display-manager") results in:
```

$ echo $DISPLAY
localhost:11.0

$ ps wwwaux | grep auth
root      3441  0.0  0.6  35212 14084 tty7     SLs+ Mar02   0:01 /usr/bin/Xorg :0 -auth /var/gdm/:0.Xauth -nolisten tcp vt7

1 $ x11vnc -localhost -nopw -once -auth /var/gdm/:0.Xauth -display :0
x11vnc version: 0.9.8 lastmod: 2009-06-14
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified
XOpenDisplay(":0") failed.
Trying again with XAUTHLOCALHOSTNAME=localhost ...
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified
***************************************
 *** XOpenDisplay failed (:0)
* x11vnc was unable to open the X DISPLAY: ":0", it cannot continue.
*** There may be "Xlib:" error messages above with details about the failure.
...

$ x11vnc -localhost -nopw -once -auth /var/gdm/:0.Xauth -display :11
05/03/2010 10:28:51 x11vnc version: 0.9.8 lastmod: 2009-06-14
X11 connection rejected because of wrong authentication.
X connection to localhost:11.0 broken (explicit kill or server shutdown).

$ x11vnc -localhost -nopw -once -auth /var/gdm/:0.Xauth -find
x11vnc version: 0.9.8 lastmod: 2009-06-14
wait_for_client: WAIT:cmd=FINDDISPLAY
initialize_screen: fb_depth/fb_bpp/fb_Bpl 24/32/2560
Autoprobing TCP port
Autoprobing selected port 5900

The VNC desktop is:      controller:0
PORT=5900
Got connection from client 127.0.0.1
other clients:
check_access: client 127.0.0.1 matches host 127.0.0.1
incr accepted_client for 127.0.0.1:59465.
wait_for_client: got client
Client Protocol Version 3.8
Protocol version sent 3.8, using 3.8
client progressed=1 in 6/5 0.071403 s
client_set_net: 127.0.0.1  0.0002
wait_for_client: running: env X11VNC_SKIP_DISPLAY=''  /bin/sh /tmp/x11vnc-find_display.Djn4vR
xauth:  timeout in locking authority file /var/gdm/:0.Xauth
wait_for_client: find display cmd failed
wait_for_client: bad reply '
'

```

(note: I've cleaned up the error messages a bit)

---

### Post by krunge on 2010-03-05
For the second link you give:
[INDENT][http://www.karlrunge.com/x11vnc/faq.html#faq-display-manager](http://www.karlrunge.com/x11vnc/faq.html#faq-display-manager)[/INDENT]
I believe you want to use the method called 'Continuously' in that FAQ, but you appear to be using the one called 'One time only'.

The 'Continuously' one will put the x11vnc cmdline in /etc/gdm/Init/Default (or similar file if KDM is your greeter) and so will start x11vnc at boot-time which I believe is what you want, no?

My guess for why 'One time only' is failing for you is because you are not running the x11vnc command as root (or sudo.)  Are you running 
```
x11vnc -localhost -nopw -once -auth /var/gdm/:0.Xauth -display :0
``` as root?

---

### Post by dargaud on 2010-03-05
Absolutely correct. It works fine now. Although the FAQ is rather long, it's actually only 2 lines to add in 2 files.

---

### Post by krunge on 2010-03-05
Good, glad it is working for you.

Note that if GDM is one's login greeter (default on ubuntu) there are some issues with the most recent GDM.  It will kill x11vnc no matter what (the GDM KillInitClients=false feature has been removed.)  So x11vnc version 0.9.9 (in debian repos, but I'm not sure if they are in ubuntu yet) now automatically tries to avoid being killed by GDM, and also avoid some other problems.

---

### Post by asmoore82 on 2010-03-05
You might want to check out this How To that I just wrote up this week:
[http://ubuntuforums.org/showpost.php?p=8913391&postcount=10](http://ubuntuforums.org/showpost.php?p=8913391&postcount=10)

---

