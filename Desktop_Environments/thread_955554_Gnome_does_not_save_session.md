---
title: "Gnome does not save session"
date: 2008-10-22
forum: Desktop Environments
---

### Post by AudioDef on 2008-10-22
I just installed Ubuntu on a laptop and even though I've configured Gnome to remember applications, it does not restart them when I restart Gnome (for example, Basket and the Korganizer applet do not come back). 

Anyone have this issue?

---

### Post by rrr0321 on 2008-11-04
I have the same issue with 8.10. Does anyone know of a fix?

---

### Post by AudioDef on 2008-11-04
I've found you can manually add them in the sessions control panel, but some things open up all their windows when Gnome starts when all I really want is the taskbar icon to be available automatically. Maybe it's just a matter of finding the right command-line switches for these programs to make that happen.

---

### Post by jminker on 2008-11-09
I also have this problem in 8.10 whereas it always worked in earlier versions.

Jim

---

### Post by pt78 on 2008-11-09
Hi, I'm also having problem with saving session. It does not work at all. I have clean installation of 8.10, in 8.04 it was fine. Only interesting thing (I'm not sure it is related to the problem.) in logs is this part of auth.log.
```
Nov  9 10:35:43 sofia gdm[5127]: pam_unix(gdm:session): session opened for user pista by (uid=0)
Nov  9 10:35:43 sofia gdm[5127]: pam_ck_connector(gdm:session): nox11 mode, ignoring PAM_TTY :0
Nov  9 10:35:43 sofia gdm[5127]: gnome-keyring-daemon: couldn't lookup keyring component setting: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://www.gnome.org/projects/gconf/ for information. (Details -  1: Failed to get connection to session: dbus-launch failed to autolaunch D-Bus session: No protocol specified
Nov  9 10:35:43 sofia gdm[5127]: Autolaunch error: X11 initialization failed.
Nov  9 10:35:43 sofia gdm[5127]: )gnome-keyring-daemon: couldn't lookup ssh component setting: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://www.gnome.org/projects/gconf/ for information. (Details -  1: Failed to get connection to session: dbus-launch failed to autolaunch D-Bus session: No protocol specified
Nov  9 10:35:43 sofia gdm[5127]: Autolaunch error: X11 initialization failed.
Nov  9 10:35:43 sofia gdm[5127]: )gnome-keyring-daemon: couldn't lookup pkcs11 component setting: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://www.gnome.org/projects/gconf/ for information. (Details -  1: Failed to get connection to session: dbus-launch failed to autolaunch D-Bus session: No protocol specified
Nov  9 10:35:43 sofia gdm[5127]: Autolaunch error: X11 initialization failed.


```

---

### Post by jkmspyksma on 2008-11-13
Ditto for me.

Saved-sessions worked in 8.04 but no longer in 8.10, despite "automatically remember running applications when logging out".

Has no one found a reason for this yet?

---

### Post by kimr1508 on 2008-11-16
I have the same problem in 8.10. 

After searching on the net, I found that for some people calling "gnome-session-save" in terminal does the trick, but that does not work for me either.

I have not tried gnome session save in 8.04 but in 7.10 it did not work for me, and I believe it has been a long time bug in Gnome according to communities on the net.

Hope it is fixed soon because it is a really nice feature - works perfectly in KDE but that's another story :)

---

### Post by pt78 on 2008-11-29
For those watching this thread: 
There is another thread with asking for solving the same problem [here](http://ubuntuforums.org/showthread.php?t=964730).
Bug is reported in [Ubuntu bug-tracker](https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/249373). But bug comes from "upstream" - GNOME. [Here is bug report](http://bugzilla.gnome.org/show_bug.cgi?id=552387). ("urgent" and "blocker", thanks)

Some workaroud can be found over here: [http://blogs.sun.com/mattman/entry/gnome_2_24_session_save1](http://blogs.sun.com/mattman/entry/gnome_2_24_session_save1)


It does not seem to be solved for Ibex (8.10). At least issue managed to get to [IntrepidReleaseNotes wiki](https://wiki.ubuntu.com/IntrepidReleaseNotes), so others will be warned.

Not much left to say. Be patient. ;)

---

### Post by lorebett on 2009-03-04
The problem is still there, in fact, if you run gnome-session-properties from the console and try to act on that option I get in the console:

> ** (gnome-session-properties:6693): DEBUG: Session saving is not implemented yet!
** (gnome-session-properties:6693): DEBUG: Session saving is not implemented yet!

I think this is quite an urgent BUG

---

