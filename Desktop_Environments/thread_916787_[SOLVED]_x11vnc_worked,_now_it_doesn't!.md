---
title: "[SOLVED] x11vnc worked, now it doesn't!"
date: 2008-09-11
forum: Desktop Environments
---

### Post by talz13 on 2008-09-11
I had x11vnc working perfectly fine for the last 2 weeks, and today it just refuses to start.  I did a fresh reboot and everything, yet it still refuses to run.

I launch it from a shell script:```
#! /bin/bash

/usr/bin/x11vnc -rfbauth /home/jeff/.vnc/passwd -o /home/jeff/.vnc/x11vnc.log -noxdamage -shared -forever -bg -rfbport 5900
```and it used to launch, then say something like ```
PORT=5900
``` after it finished launching.  Now it just sits there for a few seconds and exits with no output.  A grep of ps aux for x11 or x11* only shows my running grep, with no x11vnc process running.

A grep of ps aux | grep X shows:```
jeff@server:~$ ps aux | grep X
root      6229  0.5  0.6  95648 26328 tty7     Ss+  08:56   0:08 /usr/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7
jeff      7539  0.0  0.0   5168   856 pts/0    S+   09:21   0:00 grep X
``` so the X server is running.

The log for x11vnc shows either:```
11/09/2008 09:20:22 passing arg to libvncserver: -rfbauth
11/09/2008 09:20:22 passing arg to libvncserver: /home/jeff/.vnc/passwd
11/09/2008 09:20:22 passing arg to libvncserver: -rfbport
11/09/2008 09:20:22 passing arg to libvncserver: 5900
11/09/2008 09:20:22 x11vnc version: 0.9.3 lastmod: 2007-09-30

11/09/2008 09:20:23 ***************************************
11/09/2008 09:20:23 *** XOpenDisplay failed (localhost:10.0)

*** x11vnc was unable to open the X DISPLAY: "localhost:10.0", it cannot continue.
*** There may be "Xlib:" error messages above with details about the failure.

Some tips and guidelines:

 * An X server (the one you wish to view) must be running before x11vnc is
   started: x11vnc does not start the X server.  (however, see the
   recent -create option if that is what you really want).

 * You must use -display <disp>, -OR- set and export your $DISPLAY
   environment variable to refer to the display of the desired X server.
 - Usually the display is simply ":0" (in fact x11vnc uses this if you forget
   to specify it), but in some multi-user situations it could be ":1", ":2",
   or even ":137".  Ask your administrator or a guru if you are having
   difficulty determining what your X DISPLAY is.

 * Next, you need to have sufficient permissions (Xauthority)
   to connect to the X DISPLAY.   Here are some Tips:

 - Often, you just need to run x11vnc as the user logged into the X session.
   So make sure to be that user when you type x11vnc.
 - Being root is usually not enough because the incorrect MIT-MAGIC-COOKIE
   file will be accessed.  The cookie file contains the secret key that
   allows x11vnc to connect to the desired X DISPLAY.
 - You can explicity indicate which MIT-MAGIC-COOKIE file should be used
   by the -auth option, e.g.:
       x11vnc -auth /home/someuser/.Xauthority -display :0
       x11vnc -auth /tmp/.gdmzndVlR -display :0
   you must have read permission for the auth file.

 - If NO ONE is logged into an X session yet, but there is a greeter login
   program like "gdm", "kdm", "xdm", or "dtlogin" running, you will need
   to find and use the raw display manager MIT-MAGIC-COOKIE file.
   Some examples for various display managers:

     gdm:     -auth /var/gdm/:0.Xauth
     kdm:     -auth /var/lib/kdm/A:0-crWk72
     xdm:     -auth /var/lib/xdm/authdir/authfiles/A:0-XQvaJk
     dtlogin: -auth /var/dt/A:0-UgaaXa

   Only root will have read permission for the file, and so x11vnc must be run
   as root.  The random characters in the filenames will of course change,
   and the directory the cookie file resides in may also be system dependent.
   Sometimes the command "ps wwwaux | grep auth" can reveal the file location.

See also: http://www.karlrunge.com/x11vnc/#faq
``` indicating that an X server isn't running (which it IS running), or:```
11/09/2008 09:03:45 passing arg to libvncserver: -rfbauth
11/09/2008 09:03:45 passing arg to libvncserver: /home/jeff/.vnc/passwd
11/09/2008 09:03:45 passing arg to libvncserver: -rfbport
11/09/2008 09:03:45 passing arg to libvncserver: 5900
11/09/2008 09:03:45 x11vnc version: 0.9.3 lastmod: 2007-09-30


11/09/2008 09:03:45 Using X display localhost:11.0
11/09/2008 09:03:45
11/09/2008 09:03:45 ------------------ USEFUL INFORMATION ------------------
11/09/2008 09:03:47
11/09/2008 09:03:47 Wireframing: -wireframe mode is in effect for window moves.
11/09/2008 09:03:47   If this yields undesired behavior (poor response, painting
11/09/2008 09:03:47   errors, etc) it may be disabled:
11/09/2008 09:03:47    - use '-nowf' to disable wireframing completely.
11/09/2008 09:03:47    - use '-nowcr' to disable the Copy Rectangle after the
11/09/2008 09:03:47      moved window is released in the new position.
11/09/2008 09:03:47   Also see the -help entry for tuning parameters.
11/09/2008 09:03:47   You can press 3 Alt_L's (Left "Alt" key) in a row to
11/09/2008 09:03:47   repaint the screen, also see the -fixscreen option for
11/09/2008 09:03:47   periodic repaints.
11/09/2008 09:03:47
11/09/2008 09:03:47 XFIXES available on display, resetting cursor mode
11/09/2008 09:03:47   to: '-cursor most'.
11/09/2008 09:03:47   to disable this behavior use: '-cursor arrow'
11/09/2008 09:03:47   or '-noxfixes'.
11/09/2008 09:03:47 using XFIXES for cursor drawing.
11/09/2008 09:03:48 GrabServer control via XTEST.
11/09/2008 09:03:54
11/09/2008 09:03:54 Scroll Detection: -scrollcopyrect mode is in effect to
11/09/2008 09:03:54   use RECORD extension to try to detect scrolling windows
11/09/2008 09:03:54   (induced by either user keystroke or mouse input).
11/09/2008 09:03:54   If this yields undesired behavior (poor response, painting
11/09/2008 09:03:54   errors, etc) it may be disabled via: '-noscr'
11/09/2008 09:03:54   Also see the -help entry for tuning parameters.
11/09/2008 09:03:54   You can press 3 Alt_L's (Left "Alt" key) in a row to
11/09/2008 09:03:54   repaint the screen, also see the -fixscreen option for
11/09/2008 09:03:54   periodic repaints.
11/09/2008 09:03:54
11/09/2008 09:03:54 warning: XShm extension is not available.
11/09/2008 09:03:54 For best performance the X Display should be local. (i.e.
11/09/2008 09:03:54 the x11vnc and X server processes should be running on
11/09/2008 09:03:54 the same machine.)
11/09/2008 09:03:54 Restart with -noshm to override this.
```


Could this have anything to do with my installing Xming on this remote computer?

---

### Post by talz13 on 2008-09-11
Well, I seem to have answered my own question just now.  Since I had the "Enable X11 Forwarding" checked in my putty session, it wouldn't start.  I unchecked it and restarted my putty session and now x11vnc starts up just fine!

Hope this helps someone in the future...

---

