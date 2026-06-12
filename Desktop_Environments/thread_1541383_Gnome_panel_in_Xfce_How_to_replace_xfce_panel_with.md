---
title: "Gnome panel in Xfce? How to replace xfce panel with Gnome panel?"
date: 2010-07-29
forum: Desktop Environments
---

### Post by arapaho on 2010-07-29
Is it possible to install Gnome-panel in Xfce? I'd like to completely replace xfce-panel with gnome-panel.
It is possible the other way round so maybe this way too?
[http://ohioloco.ubuntuforums.org/showthread.php?p=7197129](http://ohioloco.ubuntuforums.org/showthread.php?p=7197129)

I tried xfce4-XfApplet-plugin but it doesn't work the way I would like to.

---

### Post by rvchari on 2011-01-29
i was also having a thought to replace xfce panel by gnome panel. i felt i could have the speed of xfce speed of window manager and its default behaviour with gnome panel that is well customised in gnome desktop !

---

### Post by hhh on 2011-01-29
Install gnome-panel and all of the cruft it pulls in with it, go to SettingsSession and Startup>Session, hi-light xfce4-panel and click the Quit Program button and then the Save Session button, open the Run dialog (Alt+F2) and run gnome-panel, log out and make sure the "Save session for future logins" button is checked.

I haven't tried this, as I (and pretty much everyone else on the planet) think xfce4-panel is better than gnome-panel, and I don't want to pull in things like gnome-menus that I'm not going to use.

I use Xfce but not Xubuntu, so I'm not sure how your menus are arranged. If you can't find that entry for "Sessions and Startup", you can bring it up with the Run dialog by entering xfce4-session-settings .

If gnome-panel doesn't start when you log back in, just add it to the list of Autostart Applications in xfce4-session-settings.

hth

---

### Post by Copper Bezel on 2011-01-29
Intriguing. I had no idea that would just work like that. (I tried the reverse instead, since XFCE does have the better panel and I use Gnome. Good to know that if, for whatever reason, I ever can't use Avant Window Navigator, the XFCE panel is an option.)

Actually ... there could be perks to having a couple of different panels to call up. Huh.

Edit: Yeah, don't do this. XFCE's panel drags along its power manager and network manager, breaking Gnome's. I restarted a couple of times and it seems to have gone away.

---

### Post by rvchari on 2011-01-30
if xfce panel can be customised like this =>
expanded panel with notifier / date / time on top right corners. top left will have a global menu applet with extreme top left having an option of window buttons to be visible when windows are maximised...

i tried to tweak xfce panel in expanded position, but i could not move the items to the top right corner..:confused:

---

