---
title: "How to copy user settings to another user?"
date: 2005-05-07
forum: Desktop Environments
---

### Post by SlugO on 2005-05-07
I just made a second user profile for my brother.
Unfortunately the resolution and theme there are using the default settings.

I'd like to know how I can copy my own settings to his profile.
Except for the home dir and password of course...
I want to copy atleast the resolution, theme, icons and menus.

Thanx to anyone who can help.

---

### Post by nemin on 2005-05-07
[QUOTE=SlugO]I just made a second user profile for my brother.
Unfortunately the resolution and theme there are using the default settings.

I'd like to know how I can copy my own settings to his profile.
Except for the home dir and password of course...
I want to copy atleast the resolution, theme, icons and menus.
[/QUOTE]
Almost all of these settings are in .* files in your home directory I guess, so you can easily copy them from your own to your brother's home.

---

### Post by XDevHald on 2005-05-07
[QUOTE=nemin]Almost all of these settings are in .* files in your home directory I guess, so you can easily copy them from your own to your brother's home.[/QUOTE]
 What you can do, is goto your **System > Preferences > Themes **and select the first tab and click **Goto Theme Directory **and click on the theme you want him to have and right click, then select **Create Archive. **

Do this same step for each tab in your Themes application in the **System > Preferences > Themes **and you can send them over to his home directory for him to have the same theme, icon and menu design as well.

---

### Post by bored2k on 2005-05-07
[QUOTE=BB]What you can do, is goto your **System > Preferences > Themes **and select the first tab and click **Goto Theme Directory **and click on the theme you want him to have and right click, then select **Create Archive. **

Do this same step for each tab in your Themes application in the **System > Preferences > Themes **and you can send them over to his home directory for him to have the same theme, icon and menu design as well.[/QUOTE]
 Yeah but the real config stay intact [like Firefox's, nautilus, etc]. That's just an eye candy tweak..

I usually do this by copying the .config files I want to my new $HOME

---

### Post by nemin on 2005-05-07
[QUOTE=BB]What you can do, is goto your **System > Preferences > Themes **and select the first tab and click **Goto Theme Directory **and click on the theme you want him to have and right click, then select **Create Archive. **

Do this same step for each tab in your Themes application in the **System > Preferences > Themes **and you can send them over to his home directory for him to have the same theme, icon and menu design as well.[/QUOTE]
Hmm that's a nice solution!:) Though I prefer the quick&dirty way, copying a few .* dirs, so you get (almost) all settings from programs too, but I don't know if the OP wants that:)

---

### Post by kosmic on 2005-05-07
or copy every file you want to apear in your new acount to -> /etc/skel, and voila.

copy the conf files of your home dir to that directory and every new user you create will have automaticaly everything equal to your principal acount excpet username and password.

---

### Post by Parsec01 on 2008-03-14
However, in order for the /etc/skel method to work, you must add a new user using the comman-line command 'useradd -m username'. If you do it via the GUI as of 7.10, this will otherwise not work!

---

