---
title: "Can't change xfce4-panel settings on new users"
date: 2012-05-16
forum: Desktop Environments
---

### Post by eath on 2012-05-16
I am running xubuntu 12.04.  I am trying to set up the panels for a dual screen setup.  All the changes made (new panel3 on monitor 2 and lauchers) all work great.  I am the original user with what-ever ubuntu calls me (there isn't root.)  Now, the second user is just a plain user.  When I make the same changes to the panel, the panel-1 changes are kept, the panel-2 changes (the dock on the bottom) are forgotten, and the new panel-3 doesn't exist after logout/login.  I looked in Settings Editor -> xfce4-panel -> panels and it shows three panels on both users.  However, the normal user isn't loading those settings.  Is there a setting I am missing? Why is panel-0 (on settings editor) loading user prefs, but not panel-1 or panel-2? 

Note: I should note that Panel-1, Panel-2, and Panel-3 in the panel gui is referenced as panel-0, panel-1, and panel-2 int the Settings Editor gui.)

I was looking at the .xml files under ~/.config/xfce4/xfconf/xfce-perchannel-xml and it was only showing two panels as well.  I don't know where the settings editor was getting its info and I don't know why the .xml kept reseting after each login.  I forgot to mention that earlier.  I've tried to reset the xfce4-panel, but can't figure how to restart it as it is still running.

---

### Post by Toz on 2012-05-16
> **eath said:**
> I am running xubuntu 12.04.  I am trying to set up the panels for a dual screen setup.  All the changes made (new panel3 on monitor 2 and lauchers) all work great.  I am the original user with what-ever ubuntu calls me (there isn't root.)  Now, the second user is just a plain user.  When I make the same changes to the panel, the panel-1 changes are kept, the panel-2 changes (the dock on the bottom) are forgotten, and the new panel-3 doesn't exist after logout/login.  I looked in Settings Editor -> xfce4-panel -> panels and it shows three panels on both users.  However, the normal user isn't loading those settings.  Is there a setting I am missing? Why is panel-0 (on settings editor) loading user prefs, but not panel-1 or panel-2?
When you log in as the new user, are there any messages in /.xsession-errors that might indicate why their not loading?

> Note: I should note that Panel-1, Panel-2, and Panel-3 in the panel gui is referenced as panel-0, panel-1, and panel-2 int the Settings Editor gui.)

I was looking at the .xml files under ~/.config/xfce4/xfconf/xfce-perchannel-xml and it was only showing two panels as well.  I don't know where the settings editor was getting its info and I don't know why the .xml kept reseting after each login.  I forgot to mention that earlier.  I've tried to reset the xfce4-panel, but can't figure how to restart it as it is still running.
To restart the panel while its running, use:
```
xfce4-panel --restart
```

---

### Post by LewisTM on 2012-05-16
To reset the panel you need to do a bit more. You need to delete file /home/<user>/.config/xfce4/xfconf/xfce-perchannel-xml/xfce4-panel.xml **outside** of Xfce such as in a virtual session (Ctrl-Alt-F1) at the graphical login prompt, or as another user (e.g. yourself) with superuser privileges. In my experience quitting xfce4-panel won't suffice, it seems like the xml file is cached in memory. Upon login a fresh xml will be created with factory defaults.

Once you're at it you could copy your own working xml file to the user's directory (change the owner with a sudo chown command) and see if that helps.

Cheers!

---

