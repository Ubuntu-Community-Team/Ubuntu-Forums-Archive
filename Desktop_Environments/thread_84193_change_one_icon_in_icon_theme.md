---
title: "change one icon in icon theme"
date: 2005-10-30
forum: Desktop Environments
---

### Post by kashms on 2005-10-30
I installed nuoveXT icon theme, but I would like to change some icons. For example I exchanged all firefox.png files with a custom icon, but the default theme icon still show up for firefox. Is there some settings I need to change when exchanging icons?

---

### Post by sethmahoney on 2005-10-30
[QUOTE=kashms]I installed nuoveXT icon theme, but I would like to change some icons. For example I exchanged all firefox.png files with a custom icon, but the default theme icon still show up for firefox. Is there some settings I need to change when exchanging icons?[/QUOTE]

You should just have to go into the folder where the icon theme is stored, which should be

/home/.icons

I think, and find the firefox icon (or whichever icon), delete it, replace it with the one you want, and then make sure it has the same name as the icon you replaced.  Oh, wait.  One more step: Open up the Theme Preferences, go to Theme Details, click the Icons tab, select a different icon theme, and then reselect the nuoveXT theme.  That *should* do it.

---

### Post by poptones on 2005-10-30
If you're trying to remove the blue firefox ball from the task list bar, you can't. You can change the default icons everywhere else, but the task bar always seems to prefer the application's icon. Oddly, it accepts the changes with gnome applications like nautilus, evolution, etc - but firefox and other "non native" applications keep their defaults.

---

### Post by sethmahoney on 2005-10-30
I have a firefox icon that isn't the blue ball (it is the default for the icon theme I'm using, like the firefox logo but all in shades of blue).  I also think there's a script somewhere to change it to the firefox logo, if that's what you want to do, but I don't remember what its called.

---

### Post by raghav_p on 2005-10-30
The instructions for changing the icon are available for Hoary on ubuntuguide. Not sure if it works for Breezy. You could try EasyUbuntu, I believe that works for changing the icons.

---

### Post by kashms on 2005-10-30
I already changed the firefox icon when using the default breezy icon theme. The instructions for that are in GNOME Help. But when I change theme to NuoveXT, it has its own firefox icon (white fox) which is the one I'm trying to change. Changing the files in the .icons did not help on that. I'll try with other icons to see if it is specific to the firefox icon.

---

