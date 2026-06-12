---
title: "Disable compiz"
date: 2007-10-01
forum: Desktop Effects &amp; Customization
---

### Post by RockinFox on 2007-10-01
Compiz freezes my computer every time i boot. I have tried to disable it by using" metacity --replace" (I get the error "unable to open X display") and "gnome-xgl-switch -disable-xgl" (I get the error"command 'gnome-xgl-switch' does not exist"). Is there another command that would disable compiz? Thanks I am a bit of linux rookie, i really would appreciate help
P.S. I am running Gutsy but i don't think that should make a difference

---

### Post by hyperair on 2007-10-01
It actually does make a difference. What you need to do is.. at the login screen, press F10. Click on Sessions and login to the Failsafe GNOME session. When you're in, open your Appearance applet (System->Preferences->Appearance or rightclick on desktop->change desktop background). Then move to the Desktop Effects tab, and disable it. Then log out, and log back into your normal session. It should have no problem loading after that.

By the way, Gutsy is a development release and you shouldn't use it (until its release about 19 days down the road) unless you have some technical knowhow about it.

---

