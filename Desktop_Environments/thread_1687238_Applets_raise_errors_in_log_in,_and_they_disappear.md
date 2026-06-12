---
title: "Applets raise errors in log in, and they disappear."
date: 2011-02-13
forum: Desktop Environments
---

### Post by perryjr on 2011-02-13
Ubuntu applets crash when loading. I login into my account and obtain a lot o fmessages saying the panel found a problem when initializing "OAFIID:GNOME_[...]" Do you want to remove the applet from you configuration?. Only the menu applet works. I cannot open items in System > Preferences too. I click all of them, but none opens. Gedit doesn't load too.

1) I've tested deleting all the .gconf, .metacity, .gconfd, etc. 
2) I've tested deletings contents in /tmp
3) I've tested reinstalling libbonobo2-0
4) I've tested reinstalling gnome-applets, gnome-applets-data and gnome-panel.
5) I've tested it with a new user... the same problem!

In my .xsession-erros apper a message for each applet saying:
Failed to initialise the ActivationContext.

I've not upgrade or update the system before the error arrive  this morning.

Some ideas? =S

---

