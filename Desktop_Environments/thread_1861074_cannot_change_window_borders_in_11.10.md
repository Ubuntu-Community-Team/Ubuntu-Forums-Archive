---
title: "cannot change window borders in 11.10?"
date: 2011-10-15
forum: Desktop Environments
---

### Post by gamblor01 on 2011-10-15
I'm not a huge fan of dark menus in the Ambiance theme, though I do prefer dark window borders instead of light window borders.  So in previous releases I have always changed the theme to Radiance, and then customized the window borders by setting them back to the Ambiance look.  However, in 11.10 the option to customize a theme seems to have disappeared entirely.

When I go to the "Appearance" panel I can only select themes from the bottom right.  There is no option to customize, and even clicking on the "All Settings" button in the top left doesn't seem to offer the option.

Does anyone know how to accomplish this?  The only stuff I can find on google so far talks about using emerald.  Isn't there a way to do this natively anymore, without the need to install 3rd party packages??

---

### Post by baronKarza on 2011-10-15
I'm looking for the same thing. At present seems that only emerald can do something. I hope there is another way...

---

### Post by mcduck on 2011-10-15
Install the [gnome-tweak-tool]("apt:gnome-tweak-tool") package. It gives you some advanced settings for Gnome 3 and allows you to select icon theme, GTK3 theme and window border themes separately from each other.

Don't expect the same level of customization, though, Gnome 3 and GTK3 are rather new and don't have all the options yet that gnome2 accumulated over the years.

---

### Post by gamblor01 on 2011-10-15
Thanks mcduck.  That works, though this seems considerably more complicated than what we had in previous releases.  The changes didn't seem to take effect immediately either -- I had to logout and then log back in.  In any case, it's setup better now.  Thanks!

---

### Post by BazookaAce on 2011-10-15
Instead of loging out and in again you can do ALT + F2, type R + Enter. Gnome-Shell will now reload.

---

