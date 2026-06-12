---
title: "Problems with X"
date: 2009-01-14
forum: Desktop Environments
---

### Post by Quorlia on 2009-01-14
Sorry for the unspecific title but I don't really know how to categorise the error.

I installed Ubuntu (8.10, downloaded and burnt two days ago!) using Wubi but haven't yet been able to log in properly using X.  The computer is about 5 years old and runs Windows XP.

First time I tried it crashed just after accepting my password and clearing the screen.  The entire local system froze and all I was able to do was move the mouse pointer (I tried CTRL-ALT-BKSP to kill the xserver, CTRL-ALT-1 to get to a command line, CTRL-ALT-DEL to reboot, even ALT-SYSREQ-B! keyboard was completely unresponsive with num lock, caps lock and scroll lock lights failing to come on)

I found some error messages which indicated that perhaps my lack of network connectivity was the problem (although I found it rather hard to believe!)  Even so when troubleshooting it is useful to have a network available so I set up the network from the commandline (wireless network using ndiswrapper) and installed openssh-server so I could log in remotely.

I then tried logging in again to Gnome.  This time I briefly got a glimpse of the top and bottom toolbars but then they seemed to scroll up and down and the system locked up.

I tried the gnome failsafe option (which also failed in the same way) although the basic failsafe terminal did give me a basic terminal.  I tried installing KDE and this seemed to show me a splash screen with what looked like space for 5 icons but only got as far as putting up 4 before the local system went unresponsive.  At this point I was already logged in using ssh but I was unable to restart X (my attempts resulted in a pretty snowstorm of red, blue and green dots :()and eventually just gave up and shut the system down.

Anyway I know this is not a terribly good post but if you tell me what information will help then I'll post it.

Thanks in advance

quorlia

---

### Post by Quorlia on 2009-01-18
After a bit of messing around I've ditched both Gnome and KDE and have become Enlightened.  I got KDE working, at snails pace (upwards of 15 seconds to open a menu etc etc), so I suspect the minimum specs are a little too minimum......

quorlia

---

