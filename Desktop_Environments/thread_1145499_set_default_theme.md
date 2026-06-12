---
title: "set default theme"
date: 2009-05-01
forum: Desktop Environments
---

### Post by gbit on 2009-05-01
I have the XPgnome theme for ubuntu, and I want to set it for all users. I am at a school with more than 2000 users, so setting each one by one would be much too time consuming and unnecessary. Is there a way to set a theme for every user on our server at one time? It has to be default so if i straight up create a new account, it will already have that certain custom theme. Thanks.

PS btw, my guess would be to patch human theme but even i'm not sure bout that. is there any theme management tools out there for this issue or is it gonna be all terminal stuff?

---

### Post by narcisgarcia on 2011-02-03
I'm also interested in setting a gnome theme from a script.

---

### Post by mcduck on 2011-02-03
Take a look at [http://live.gnome.org/Sabayon/]("http://live.gnome.org/Sabayon/"), Gnome's admin tool for configuring desktop settings for users. (available in Software Center as "User Profile Editor")

Also simply running gconf-editor as root, setting the GTK theme and then setting that key as mandatory should work as well. But Sabayon is most likey the easier & better way to do this.

(You can also do some settings for new users by placing the relevant configuration files into /etc/skel. Although that doesn't force the settings, only sets the defaults the newly created users have. Everything in /etc/skel will be copied to any new user's home)

edit: if you want to set the theme from a script, just use *gconftool* to set the correct gconf key.

---

### Post by narcisgarcia on 2011-02-03
Ok, I see the current Gnome theme name with this command:
```
gconftool --get /desktop/gnome/interface/gtk_theme
```
And I can set the theme name with this command:
```
gconftool --type=string --set /desktop/gnome/interface/gtk_theme "Clearlooks"
```

But theme is not completely set. Keys such as "gtk_color_scheme" or "icon_theme" are not updated with theme profile/data.
Somethig changes on the desktop, it's true, but only part of theme properties.

---

### Post by mcduck on 2011-02-03
> **narcisgarcia said:**
> Ok, I see the current Gnome theme name with this command:
```
gconftool --get /desktop/gnome/interface/gtk_theme
```
And I can set the theme name with this command:
```
gconftool --type=string --set /desktop/gnome/interface/gtk_theme "Clearlooks"
```

But theme is not completely set. Keys such as "gtk_color_scheme" or "icon_theme" are not updated with theme profile/data.
Somethig changes on the desktop, it's true, but only part of theme properties.

That's because those aren't part of the GTK theme (which that key sets).

GTK theme only affects how the applications look like, widgets,buttons, scrollbars and such. Icon theme is a separate thing, and so is the theme for whatever window manager you might be using. So you need to set the keys for all those.

edit: If you use the default setup of Ubuntu, then the window border theme is set in apps/metacity/general/theme, and icons in desktop/gnome/interface/icon_theme. I can't right now remember what the key for custom colors is, you might want to browse around with the gconf-editor to find it....

---

