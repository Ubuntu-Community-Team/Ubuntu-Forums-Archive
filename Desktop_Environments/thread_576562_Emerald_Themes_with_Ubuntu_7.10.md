---
title: "Emerald Themes with Ubuntu 7.10"
date: 2007-10-15
forum: Desktop Environments
---

### Post by alligoodw on 2007-10-15
I've upgraded Ubuntu 7.4 with Ubuntu 7.10 - I'm very impressed.  Correct me if I'm wrong, but I believe Emerald Themes Manager controls window borders.  If so, I'm having a problem changing my borders with this release.  

First of all, I only have one theme there.  All other desktop changes seem to work well.  If I modify the only theme available with the Emerald Theme Manager nothing happens.  Well, to be perfectly honest here, the border completely disappears. I'm willing to admit right up front this could be user error.  I'm still trying to learn the Linux operating system and how it works.  

At the moment, I'm not sure if something is missing from my installation, or if I'm not using the new compiz-fusion correctly.  Hopefully, someone out there will be able to direct me to good documentation on desktop management, or will be able to solve my problem.  

Your input or advise is certainly welcome.  Thanks in advance.

---

### Post by Dr. Nick on 2007-10-15
type 

emerald --replace

into a terminal and see if the emerald manager changes then.

Not sure in your case, but you may still be using metacity. Metacity is the gnome default and is not transparent or anything special. If you have no borders then type this in a terminal to get some back if emerald doesnt work

metacity --replace

---

### Post by JBAlaska on 2007-10-15
The same happened to me when I upgraded to Gutsy, To get the themes to change you have to run the command Dr. Nick suggested.

You might want to create a launcher with the command ```
emerald --replace
``` then you can click on it when you change themes.

To get emerald to run automatically, go to "advanced desktop effects settings" and add ```
emerald
``` to the plugin "window decorations" in the command box.

---

### Post by konungursvia on 2007-10-16
Yeah I must have still been using metacity, and still am I think. I upgraded to gutsy by changing feisty to gutsy in repos and doing aptitude upgrade. WHen i did this

$ metacity --replace
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"
Window manager warning: Lost connection to the display ':0.0';
most likely the X server was shut down or you killed/destroyed
the window manager.

That's what happened. Can I remove metacity? Is there another solution? Thanks

---

### Post by Dr. Nick on 2007-10-16
> **konungursvia said:**
> Yeah I must have still been using metacity, and still am I think. I upgraded to gutsy by changing feisty to gutsy in repos and doing aptitude upgrade. WHen i did this

$ metacity --replace
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"
Window manager warning: Lost connection to the display ':0.0';
most likely the X server was shut down or you killed/destroyed
the window manager.

That's what happened. Can I remove metacity? Is there another solution? Thanks

removing metacity, if possible, is not a real good idea. emerald still can get buggy and metacity is a good fallback

The method you used to upgrade is no longer recommended i believe. That method used to work great, but later releases it seems troublesome.

I would launch a terminal and run

gksu update-manager -c -d

Then install a new release if it provides the option, or if not just install any updates it shows. It sorta looks like your missing pieces

---

### Post by konungursvia on 2007-10-16
I did that first, but update manager said there was nothing to upgrade to... even with -d for development flagged.  I had no sound, and tried and tried, so decided to follow another ubuntu user who did my old method and said it worked. And it did, except metacity can't seem to make window borders, nor can emerald. :(

---

