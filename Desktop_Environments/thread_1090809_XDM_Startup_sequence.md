---
title: "XDM Startup sequence"
date: 2009-03-08
forum: Desktop Environments
---

### Post by starfry on 2009-03-08
Hi, I have a set-up that works, but I don't know why it works and that makes me feel uncomfortable ;)

I have a minimal install (command line from alternate CD) with xdm and openbox on it.

I run an X server on another box and connect it to the xdm. When I log in it starts Openbox.

How does it know to start Openbox ?

I want it to but I never told it how, so how does it know?

I've looked for configuration files, etc, but I don't know the answer...

---

### Post by starfry on 2009-03-08
Funny how, just after posting, you find the solution :)

For anyone interested...

It starts Openbox as expected because there was nothing to get in the way of defaults. The start up sequence is as follows:

   * xdm executes /etc/X11/xdm/Xsession
   * which executes /etc/X11/Xsession
   * which executes /etc/X11/Xsession.d/50x11-common_determine-startup
   * which executes /usr/bin/x-window-manager
   * a symlink to /etc/alternatives/x-window-manager
   * a symlink to /usr/bin/openbox-session
   * which executes, if present, ~/.config/openbox/autostart.sh
   * and then executes /usr/bin/openbox

---

