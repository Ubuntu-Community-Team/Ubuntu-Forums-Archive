---
title: "[SOLVED] Cairo / Gnome issues"
date: 2008-12-17
forum: General Help
---

### Post by davidself1001 on 2008-12-17
I successfully had Cairo-dock working and decided to turn off the Gnome panel by following instructions provided in another thread.  I said to remove the Gnome panel from Startup and Current sessions.  I did not find a Gnome pane in the Startup section but did remove the one from the current sessions tab.  I restarted my PC and the panel was gone.  However, now I can't launch any programs from the dock.  I have the applet that let's me go back to the Sessions preference but when I select anything from that menu nothing happens.  I have obviously screwed something up.  Help please!

---

### Post by davidself1001 on 2008-12-17
Another piece of info.  If I start up in failsafe GNOME then everything works and the panel is still there.  Where do I look to find out what I messed up?  (is that vague enough for ya).  I am a desperate man.  Please somebody help!  Another thing which is perhaps a deeper problem is that I can't use any keyboard commands either.  I tried ALT/F2 to bring up the run command to try to restart panel and it doesn't come up either so I have a deeper problem.  Some kind of command interpreter is not running or some such.  Help

---

### Post by davidself1001 on 2008-12-17
Also noticed than none of my desktop icons appear either.  That's alot of clues so hopefully someone will have the answer.

---

### Post by davidself1001 on 2008-12-17
Found this in my /var/log/gdm directory.  Does the error below relate to my problem?

Release Date: 5 September 2007
X Protocol Version 11, Revision 0
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9.2)
Current Operating System: Linux david-desktop 2.6.24-22-generic #1 SMP Mon Nov 24 18:32:42 UTC 2008 i686
Build Date: 13 June 2008  01:08:21AM
 
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Dec 17 14:48:01 2008
(==) Using config file: "/etc/X11/xorg.conf"
(II) Module "ramdac" already built-in
expected keysym, got XF86KbdLightOnOff: line 70 of pc
expected keysym, got XF86KbdBrightnessDown: line 71 of pc
expected keysym, got XF86KbdBrightnessUp: line 72 of pc
expected keysym, got XF86KbdLightOnOff: line 70 of pc
expected keysym, got XF86KbdBrightnessDown: line 71 of pc
expected keysym, got XF86KbdBrightnessUp: line 72 of pc

---

### Post by davidself1001 on 2008-12-17
So what specific log file should I look at to see where is problem originates.  I assume it must have something to do with the Session change that I made but who nows.  There are a lot of options.  What file contains the sessions information?

---

### Post by Ng Oon-Ee on 2008-12-17
Can't directly help you, but I know that keyboard shortcuts are handled by metacity. If Compiz is running it should already call metacity, by default.

I'd suggest using failsafe to alter your sessions back to what it was.

---

### Post by davidself1001 on 2008-12-17
Thanks for the metacity help.  I only removed a current session item (gnome-panel...) so I don't know what started that process to begin with.  Gnome-panel is not in the startup list even in failsafe mode. I read that you can get a clean slate by deleting .gnomef, .gnome2, .gconf and .metacity from your home directory.  I verified that if I created a new login that it came up fine but missing all of my desktop enhancements.  What would happen if I only deleted .metacity?

---

