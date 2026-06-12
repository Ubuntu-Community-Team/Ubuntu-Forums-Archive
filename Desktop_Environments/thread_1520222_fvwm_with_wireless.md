---
title: "fvwm with wireless"
date: 2010-06-29
forum: Desktop Environments
---

### Post by webwiz on 2010-06-29
Greetings Ubuntu Community

I have a fresh desktop install ubuntu 10.04 which then I added the fvwm-crystal package (and dependencies).   I logout of gnome, and into fvwm.  When I do so, I lose my wireless connection that was started when I was in gnome.

Is there a way to get a wireless manager to function inside fvwm (if I add it to the auto-start in my fvwm2rc?).  What app can I use?  I tried and failed miserably using the command line iwconifg/iwlist tools.

Thank you

JT

---

### Post by noahlt on 2010-06-29
You want to run nm-applet to control your wireless connection.  nm-applet doesn't run as a standalone program, you have to run it inside some sort of dock/panel program like gnome-panel.  It's been a long time since I've used Fvwm, but FvwmButtons can act as a dock for other programs (the way gnome-panel does).

I've never used Fvwm-Crystal, so I don't know what its configuration is like, but when learning to edit my .fvwmrc I found it useful to read Tavis Ormandy's .fvwmrc file.  Hope this helps!

---

### Post by jpkotta on 2010-07-04
> **noahlt said:**
> You want to run nm-applet to control your wireless connection.  nm-applet doesn't run as a standalone program, you have to run it inside some sort of dock/panel program like gnome-panel.  It's been a long time since I've used Fvwm, but FvwmButtons can act as a dock for other programs (the way gnome-panel does).

I've never used Fvwm-Crystal, so I don't know what its configuration is like, but when learning to edit my .fvwmrc I found it useful to read Tavis Ormandy's .fvwmrc file.  Hope this helps!

You can get a stand-alone system tray application.  I don't use one, but I have heard of stalone tray and trayer.  I thought that nm-applet had a mode where it didn't need a system tray, but I haven't used it for a long time so that might not be true any more (if it ever was).  I don't think FvwmButtons works like a system tray.  It could swallow a system tray application though.

I use wicd, which is in the repos and is packaged such that it replaces network-manager.  You can start wicd-client from fvwm with the command 
```
Exec exec wicd-client -n
```  You can bind the command to a menu item, a key, an FvwmButton, etc.

---

