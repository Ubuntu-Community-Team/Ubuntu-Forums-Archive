---
title: "Where is compiz!?"
date: 2007-12-18
forum: Desktop Effects &amp; Customization
---

### Post by CLUGENHEIM on 2007-12-18
Well, Ubuntu told me there were updates, and in the list of updates, compiz was in there. I downloaded and it installed. Or so I think. I can't find it ANYWHERE, and when I went to Add/Remove, I couldn't find it under "installed programs" or whatever. What's up here? Do I need to install it manually?

---

### Post by ThaRabbit on 2007-12-18
Try checking here:

System -> Preferences -> Appearance

There should be a tab "Visual Effects" or something like that, I'm using the dutch version of Ubuntu 7.10 so I can't be sure of the words here :)

You could always start the package manager and search on "compiz". That should immediately show you if the package is installed.

Furthermore, if you want to adjust the various effects, try installing the compizconfig-settings-manager package from the official repositories.

That package should represent itself as a shortcut under System -> Preferences -> Advanced Desktop Effect Settings

Enjoy :)

---

### Post by CLUGENHEIM on 2007-12-18
Thanks, but when I try doing anything under the "Visual Effects" tab, an error pops up, and actually while I was typing this, the "Appearance Preferences" thing just froze on me and won't close. -_________-

---

### Post by ThaRabbit on 2007-12-18
Seems you may be missing some essential compiz packages.

If you're using Ubuntu with Gnome (just making sure here): You'll need the following packages installed:
compiz
compiz-core
compiz-gnome
compizconfig-settings-manager

And for added fun:
compizconfig-fusion-plugins-main
compizconfig-fusion-plugins-extra

The dependencies should sort the rest of the requirements.

Try opening your package manager to see if you have these packages installed, if not.. install them and try again?

---

### Post by CLUGENHEIM on 2007-12-18
> **ThaRabbit said:**
> Seems you may be missing some essential compiz packages.

If you're using Ubuntu with Gnome (just making sure here): You'll need the following packages installed:
compiz
compiz-core
compiz-gnome
compizconfig-settings-manager

And for added fun:
compizconfig-fusion-plugins-main
compizconfig-fusion-plugins-extra

The dependencies should sort the rest of the requirements.

Try opening your package manager to see if you have these packages installed, if not.. install them and try again?

Yes, all of that is installed. 

Is there something I have to do to make it run?

---

### Post by Steveway on 2007-12-18
What exactly does the error message that you get say?
Also what graphics-card do you have?
Always give as much and detailed informations that you can.

---

### Post by ThaRabbit on 2007-12-18
Also, do you have the correct drivers installed and working for your graphics card?

---

### Post by machosos on 2007-12-20
how can you tell if you have the correct video driver installed?

I have a NVIDIA 6800 FXGO Ultra and installed NVidia binary X.Org driver ('new' driver) from the add/remove...is this the correct one?

I can only get a few things from compiz to work

---

