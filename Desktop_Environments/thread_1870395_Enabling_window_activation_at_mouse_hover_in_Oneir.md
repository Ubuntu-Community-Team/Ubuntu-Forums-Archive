---
title: "Enabling window activation at mouse hover in Oneiric Ocelot"
date: 2011-10-27
forum: Desktop Environments
---

### Post by travkilde on 2011-10-27
Hi there,

I recently was able to throw aside Windows and go back to Ubuntu again. (Thank you, lord. It has been six tough months!) Alas, the whole Gnome 3 implementation has taken me a bit by surprise.

Can anyone please help me find where to enable the x-mouse? That is, the activation of a window by moving the mouse over it?

It used to be in System > Preferences > Windows or thereabout, but I'm seriously stuck finding it in the new layout! What's with all the constant reorganization, anyway? :)

---

### Post by mfaber on 2011-10-29
You have to install compizconfig-settings-manager (ccsm) before by:
apt-get install compizconfig-settings-manager

Description of ccsm I find in (similar must be somewhere in English)
[http://wiki.ubuntuusers.de/Compiz_CCSM](http://wiki.ubuntuusers.de/Compiz_CCSM)
[http://wiki.ubuntuusers.de/Compiz_Plugins](http://wiki.ubuntuusers.de/Compiz_Plugins)
[http://wiki.ubuntuusers.de/CCSM_Benutzung](http://wiki.ubuntuusers.de/CCSM_Benutzung)

Then you call General Options in ccsm
You go there to Focus & Raise Behaviour

There you put your options, e.g. (sorry, my descriptions are in German and translation is probably not correct):
Change focus by clicking: No
In foreground by clicking: No
Automatic in forground: Yes
Possibly decrease "Delay to take automatically to the foreground" to 500

Eventually restart the window manager by a new login.

---

### Post by travkilde on 2011-11-03
Thanks, mfaber. Strange that these things have been removed from the general install, but great that they are still available. Thanks again!

---

