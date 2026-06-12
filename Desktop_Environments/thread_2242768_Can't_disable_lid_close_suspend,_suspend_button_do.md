---
title: "Can't disable lid close suspend, suspend button does nothing"
date: 2014-09-03
forum: Desktop Environments
---

### Post by Sotai on 2014-09-03
The lid settings in xfce4-power-manager seem to do nothing to change the lid close behavior.

note: Editing /etc/systemd/logind.conf disables lid close suspend, but when I close the lid I then get a blank (black) screen, and the xfpm lid close settings still do nothing anyway (don't lock the screen).

Also, the suspend button on the laptop does nothing in either case.

I upgraded from 12.04 and this all worked fine there, so it's some kind of regression.

---

### Post by Toz on 2014-09-04
Hello and welcome to the forums.

>  The lid settings in xfce4-power-manager seem to do nothing to change the lid close behavior.
This is a known bug and should be fixed in the next version of Xubuntu (hopefully the changes will be back-ported to this version since its LTS). Its a result of the integration of components of systemd into the Ubuntu architecture but the version of xfce4-power-manager shipped not being updated to deal with it. 

> note: Editing /etc/systemd/logind.conf disables lid close suspend, but when I close the lid I then get a blank (black) screen, and the xfpm lid close settings still do nothing anyway (don't lock the screen).
The screen locking would be a function of the screen saver. Look at the light-locker settings in the Settings Manager to see if its set to lock the screen. Since you've upgraded, also make sure that you don't have 2 screensavers running (xscreensaver and light-locker). If you do, you should probably disable one as they are just going to get in each other's way.

> Also, the suspend button on the laptop does nothing in either case.
The suspend keyboard button or the suspend menu item? Or both?

---

### Post by Sotai on 2014-09-07
> **Toz said:**
> Hello and welcome to the forums.


This is a known bug and should be fixed in the next version of Xubuntu (hopefully the changes will be back-ported to this version since its LTS). Its a result of the integration of components of systemd into the Ubuntu architecture but the version of xfce4-power-manager shipped not being updated to deal with it.

Good to know. Thanks.

> The screen locking would be a function of the screen saver. Look at the light-locker settings in the Settings Manager to see if its set to lock the screen. Since you've upgraded, also make sure that you don't have 2 screensavers running (xscreensaver and light-locker). If you do, you should probably disable one as they are just going to get in each other's way.

I have uninstalled xscreensaver. As far as the power manager, what I am talking about are the 'When laptop lid is closed' option. One of the selections is to lock the screen instead of suspend.

> The suspend keyboard button or the suspend menu item? Or both?

The suspend menu item works. The keyboard button doesn't.

---

