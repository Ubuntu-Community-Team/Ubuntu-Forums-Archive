---
title: "tsclient fullscreen and multiple desktops"
date: 2007-09-29
forum: Desktop Effects &amp; Customization
---

### Post by dartanion on 2007-09-29
I've been searching all over the place for an answer to this for an hour or so with no luck. I'm running 7.10 with Compiz running, but when I fire up a fullscreen rdp session it takes over all the viewports/desktops, when I rotate the cube all I see is that one rdp session.  Is there a way to restrict it to a single viewport/desktop?

---

### Post by dartanion on 2007-09-30
Ok, it seems to be something with the clients and running full screen. Running rdesktop and using the native screen resolution solves the problem. If tsclient or Gnome-rdp gave the option for the native resolution on my laptop I would have used that instead.

---

### Post by 206bruce on 2007-10-12
I encountered the same dilema and found the same workaround (rdesktop -g WxH).  Maybe there's a way to add our desired resolution into tsclient.  

Is there a config file for tsclient?  Anyone?

---

### Post by 206bruce on 2007-10-12
Okay, i found the tsclient config file; it's hidden in the home directory under the folder name .tsclient; (~/.tsclient).  However even after I manually changed the resolution to 1680 width, it still wouldn't take it.  

I'll just settle with a rdesktop launcher with all my preferred options...case close.

---

