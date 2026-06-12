---
title: "If you're using screenlets and they stopped working..."
date: 2007-05-18
forum: Desktop Effects &amp; Customization
---

### Post by xarmian on 2007-05-18
I found after a couple restarts screenlets stop working.. They are still loading, but they aren't displaying at all..  After some testings i've found what's causing the problem, and come up with some temporary ways to fix it.  I know I've seen some posts about screenlets that stop working, so I thought I'd share..

The problem seem to happen when switching between window managers.. For example if you normally use Beryl and you add your screenlets when using Beryl, and then switch to Metacity.. or, if Beryl crashes and reverts back to metacity automatically (which happens quite often when my computer starts, probably once every 4-5 starts)..  Then all of a sudden the screenlets are gone, they wont load unless I reload them from backup or re-add them completely.

To understand this we need a little background.. The information about your screenlets (which ones to load and their attributes) are stored in text files in ~/.config/Screenlets .. one file (screenletsd.ses) holds the name of each screenlet and the name of the config file for the screenlet.. the config files have random names, like "NG8lAwHaIJhTaw4h.state" for my TemperatureScreenlet.  This file contains a bunch of information, for example mine looks like:

> 
scale=1.0
theme_name=default
is_sticky=True
is_widget=True
keep_above=True
keep_below=False
y=332
x=989


The X and Y values store the coordinates for where the screenlet displays on your screen.  When Beryl crashes and reverts to metacity (or possibly another window manager, depending what you're using), the X/Y coordinates get screwy ("mutilated" is more like it) which causes the X coordinate in your screenlet to get messed up and become something excessively large (3000-4000 in my case).  This causes your screenlet to go off-screen, and the setting is automatically saved by the screenlets daemon.

So how do you fix it?  There is no permanent fix yet, until the code is fixed to resolve the bug.. but we can fix it temporarily by not allowing these changes to be written when metacity starts. The key is to situate your screenlets exactly how you want them, and then write-protect the configuration files so the screenlets daemon does not change the settings..  So do the following:

1) Get your screenlets exactly how you want them.. while you will be able to  move them during a session, once X restarts or your session ends the settings will revert back to how they were before you made any changes.

2) Chmod the files to make them read-only.. At the command line you would type the following:

> 
chmod 444 ~/.config/Screenlets/*


Now if you want to make changes, you have to make the screenlets writable again by typing:

> 
chmod 644 ~/.config/Screenlets/*


Once you're done making changes, re-do step 2.

I know this isn't an ideal situation, but it makes screenlets usable until the bug is fixed..  Good luck.

-Dave

---

