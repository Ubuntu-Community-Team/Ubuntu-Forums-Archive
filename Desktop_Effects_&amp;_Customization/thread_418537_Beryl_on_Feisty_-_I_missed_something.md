---
title: "Beryl on Feisty - I missed something?"
date: 2007-04-22
forum: Desktop Effects &amp; Customization
---

### Post by cogadh on 2007-04-22
Okay, I just installed Beryl on a clean install of Feisty by following the nVidia 1-2-3 method on the Beryl site: [http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_nVidia](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_nVidia)

The install ran fine, I restarted the xserver and the Beryl Manager is running, but if I try to launch Beryl as my window manager, it silently fails and goes right back to Metacity. The so-called "New User Guide" on the Beryl site is completely useless (it has more editorial comments than actual new user info) and I didn't find anything by searching here. I know I just missed something stupid that is keeping it from working, so if anyone has a suggestion, I would appreciate it.

Specs:
P4 2.0 GHz
1 GB RAM
Geforce FX 5200 256MB (9631 driver)

EDIT - Sorry, I just realixed I put this in the wrong forum. Could one of the mods move this over to the Desktop Effects forum?

---

### Post by pepsi_max2k on 2007-04-22
xgl or aiglx not enabled? try following something like [https://help.ubuntu.com/community/BerylOnEdgy?](https://help.ubuntu.com/community/BerylOnEdgy?)

---

### Post by cogadh on 2007-04-22
Thanks for pointing me to that, I wish I had seen it sooner.

Followed that guide to the letter (except for the letters that said "Edgy", replaced them with "Feisty") and it didn't work. I did find a problem with the nVidia driver that I fixed by updating to the 9755 driver, but Beryl still silently crashes.

Any other suggestions?

---

### Post by Ender Black on 2007-04-22
If you have 9755 working nicely have you tried remove and purge of beryl and downloading from Ubunutu repositories via synaptic.  Mine just worked out of the box when I switched over to Feisty.

---

### Post by cogadh on 2007-04-22
When you installed via Synaptic, which packages did you choose and which repository did you get them from?

---

### Post by cogadh on 2007-04-22
Thanks for the help guys, I figured it out. I had Composite disabled in my xorg.conf. Like I said, I'm sure I missed something stupid...

---

### Post by Ender Black on 2007-04-22
From the Miscellaneous - Graphical (universe) I chose:

beryl
beryl-core
beryl-defaults
beryl-manager
beryl-plugins
beryl-plugins-data
beryl-plugins-unsupported
beryl-plugins-unsupported-data
beryl-plugins-unsopported-dbg
beryl-settings
beryl-settings-bindings

Wow.. I didn't know how many I had... I wonder if I have too much and go with a lighter load.....

---

