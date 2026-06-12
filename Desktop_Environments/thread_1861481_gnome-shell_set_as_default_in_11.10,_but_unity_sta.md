---
title: "gnome-shell set as default in 11.10, but unity starts instead"
date: 2011-10-15
forum: Desktop Environments
---

### Post by wtc on 2011-10-15
Hello there,

After upgrade from 11.04 to 11.10 i didn't want to use unity but gnome-shell instead, so installed gnome-shell and gnome-core via apt-get.

I cannot get gnome-shell to load as default. After booting, Unity loads automatically (my user is set to auto-login), with background that I have set for gnome-shell! If I log-off and check user properties, Unity is set as default without me choosing it. If I select Gnome and log-in, gnome-shell loads - but next time system boots again into unity.  

Somebody told in forums to set gnome-shell in /desktop/gnome/session/required_components, well /required_components is not a folder shown in gconf-editor at all.

Any help?

Thanks

---

### Post by BazookaAce on 2011-10-15
Hmm, i'm also using Gnome-Shell and GS is set as the default session on my computer. Don't really know why it's not on yours though.

---

### Post by Krytarik on 2011-10-15
If you are using LightDM as the desktop manager - which is the default - , please see this guide how to change its auto-login settings:

[http://www.tuxgarage.com/2011/09/setting-lightdm-to-auto-login-oneiric.html](http://www.tuxgarage.com/2011/09/setting-lightdm-to-auto-login-oneiric.html)

Regards.

---

### Post by wtc on 2011-10-20
yes, editing lightdm.conf file helped - no idea why this didn't work with GUI.

thanks and regards

---

### Post by robin_s on 2011-10-20
None of the suggested solutions seem to work for me :(
Whatever I choose via the "gearwheel" when I log in, I get Unity 2D.
What I really wanted was gnome-shell, but that didn't seem to work, so just to see what happened I also tried installing xubuntu and XFCE.  Independent of what I selected when logging in, Unity 2D was started.  Logging out and/or rebooting the machine has so far made no difference.

This sounds like there must be something really basic which I am doing wrong.  Any suggestions?

Hope someone has a good idea...

---

### Post by phasegen on 2011-10-20
Make sure gnome-shell is installed via the software center or synaptic, then paste this in a terminal:

sudo /usr/lib/lightdm/lightdm-set-defaults -s gnome-shell

---

### Post by KalebZen on 2012-10-04
Make sure compiz-fusion-icon is not running at start up, or it will kill gnome-shell.

---

