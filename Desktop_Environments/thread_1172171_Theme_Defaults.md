---
title: "Theme Defaults"
date: 2009-05-28
forum: Desktop Environments
---

### Post by Z3ro3X on 2009-05-28
I all ready know how to change the background and the theme to Clearlooks.  What I want to know, is how to change the main menu icon back to the default gnome foot.

I also want my normal System menu (it was changed in 9.04) back with the log off and shutdown options.  I don't like the applet in the panel for doing that but I'm stuck with it as my only way to log off, shutdown and reboot.

For the most part I want all gnome settings to their upstream gnome defaults instead of ubuntu's customized settings.  This also includes the the box that pops up in the top right of my screen to alert me to things.  It's black no matter what theme I choose.  I want that to the gnome default as well.

Thanks in Advance

---

### Post by mcduck on 2009-05-28
> **Z3ro3X said:**
> I all ready know how to change the background and the theme to Clearlooks.  What I want to know, is how to change the main menu icon back to the default gnome foot.

I also want my normal System menu (it was changed in 9.04) back with the log off and shutdown options.  I don't like the applet in the panel for doing that but I'm stuck with it as my only way to log off, shutdown and reboot.

For the most part I want all gnome settings to their upstream gnome defaults instead of ubuntu's customized settings.  This also includes the the box that pops up in the top right of my screen to alert me to things.  It's black no matter what theme I choose.  I want that to the gnome default as well.

Thanks in Advance
For the logout options, simply remove the User Swicher-applet from your panel and the shutdown/reboot options will appear in the System menu.


The menu icon depends on your current icon theme, so you have to browse to your icon theme directory and then you'll find the icon in /places/start-here.png

---

### Post by Z3ro3X on 2009-05-28
> **mcduck said:**
> For the logout options, simply remove the User Swicher-applet from your panel and the shutdown/reboot options will appear in the System menu.


The menu icon depends on your current icon theme, so you have to browse to your icon theme directory and then you'll find the icon in /places/start-here.png

Awesome, thanks!

As for the icon I just figured out one option. I copied /usr/share/pixmaps/gnome-logo-icon-transparent.png to /home/z3ro3x/.icons/Mist/scalable/places/start-here.png

I know Mist isn't the default gnome icons but the blue icons look better with my background.  I decided to go with a customized Unity theme.  All I changed in that theme are the icons and cursors.  I choose the whiteglass for my mouse cursors.  Here's a screenshot.

[IMG]http://lh4.ggpht.com/_FxDFfcxQSp0/Sh5vCBnpToI/AAAAAAAAABI/An9eWoOBKCE/s800/Screenshot.png[/IMG]

---

