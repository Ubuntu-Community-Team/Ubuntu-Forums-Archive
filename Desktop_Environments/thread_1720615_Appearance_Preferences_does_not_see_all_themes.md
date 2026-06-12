---
title: "Appearance Preferences does not see all themes"
date: 2011-04-03
forum: Desktop Environments
---

### Post by Keith_Beef on 2011-04-03
So, when I go to System - Preferences - Appearance, I get the theme tab, with only nine themes listed:
[LIST]
[*]Custom,
[*]Ambiance,
[*]Clearlooks,
[*]Dust,
[*]Dust Sand,
[*]High Contrast Inverse,
[*]High Contrast Large Print Inverse,
[*]New Wave,
[*]Radiance.
[/LIST]

So I select Get more themes online and this opens up art.gnome.org/themes/metacity in Firefox.

I select a new theme, e.g. Clearlooks, and the a dialog tells me I'm about to download a tar.gz file. I choose to open with Theme Installer, and then to use this new theme.

But it does not appear in the list of themes in the preferences dialog... I see just the nine that I had before.

When I look in /usr/share/themes/ I find a whole slew of themes... 

```
$ ls -al
total 116
drwxr-xr-x  27 root root  4096 2010-10-07 12:09 .
drwxr-xr-x 339 root root 12288 2011-03-27 11:27 ..
drwxr-xr-x   3 root root  4096 2010-10-07 12:01 AgingGorilla
drwxr-xr-x   4 root root  4096 2011-03-09 23:38 Ambiance
drwxr-xr-x   3 root root  4096 2010-10-07 12:01 Atlanta
drwxr-xr-x   3 root root  4096 2010-10-07 12:01 Bright
drwxr-xr-x   4 root root  4096 2010-10-07 12:07 Clearlooks
drwxr-xr-x   4 root root  4096 2010-10-07 12:07 ClearlooksClassic
drwxr-xr-x   4 root root  4096 2010-10-07 12:06 Crux
drwxr-xr-x   3 root root  4096 2010-10-07 12:00 Default
drwxr-xr-x   4 root root  4096 2010-10-07 12:07 Dust
drwxr-xr-x   4 root root  4096 2010-10-07 12:07 Dust Sand
drwxr-xr-x   3 root root  4096 2010-10-07 12:00 Emacs
drwxr-xr-x   3 root root  4096 2010-10-07 12:01 Esco
drwxr-xr-x   3 root root  4096 2010-10-07 12:06 HighContrastInverse
drwxr-xr-x   4 root root  4096 2010-10-07 12:06 HighContrastLargePrintInverse
drwxr-xr-x   3 root root  4096 2010-10-07 12:06 Industrial
drwxr-xr-x   4 root root  4096 2010-10-07 12:07 Inverted
drwxr-xr-x   3 root root  4096 2010-10-07 12:01 Metabox
drwxr-xr-x   3 root root  4096 2010-10-07 12:06 Mist
drwxr-xr-x   4 root root  4096 2010-10-07 12:07 New Wave
drwxr-xr-x   3 root root  4096 2010-10-07 12:07 New Wave Dark Menus
drwxr-xr-x   4 root root  4096 2011-03-09 23:38 Radiance
drwxr-xr-x   3 root root  4096 2010-10-07 12:00 Raleigh
drwxr-xr-x   3 root root  4096 2010-10-07 12:06 Redmond
drwxr-xr-x   4 root root  4096 2010-10-07 12:07 Simple
drwxr-xr-x   3 root root  4096 2010-10-07 12:06 ThinIce
```


Why don't these show up in the preferences?

---

### Post by Frogs Hair on 2011-04-03
Not all themes appear in the theme window , use the customize to locate the theme components .

---

### Post by Krytarik on 2011-04-03
As an explanation, any themes that have a valid "index.theme" file in their root directory, are getting shown in the "Theme" main menu, thus without needing to choose it through "Customize".

Greetings.

---

