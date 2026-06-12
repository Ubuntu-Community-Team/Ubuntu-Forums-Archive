---
title: "Themes are infuriarating"
date: 2007-11-12
forum: Desktop Effects &amp; Customization
---

### Post by Lotekx on 2007-11-12
Hi, I am trying to install this theme [http://www.gnome-look.org/content/show.php/KOREMIN+Emerald+Compiz-Fusion+theme?content=65646](http://www.gnome-look.org/content/show.php/KOREMIN+Emerald+Compiz-Fusion+theme?content=65646)


I tried putting it in the /usr/share/emerald/theme folder, but it says I don't have permission. What should I do? Thanks.

---

### Post by kngcrntrd on 2007-11-12
Try this:

Download the Emerald theme file.  Go to System, Preferences, Emerald Theme Manager.  Click "Import".  Navigate to the location of the file you downloaded and select it.  Click "Open".  Your new theme should be installed.  You may have to select it from the list of available themes.

---

### Post by z0phi3l on 2007-11-12
Yes, manually placing the theme in the folder doesn't work, you have to use Emerald to import the theme for it to work, don't know why it's like that.

---

### Post by kngcrntrd on 2007-11-12
Also, when moving files into folders without adequate permissions, try:

Open Terminal.
Type something like:  sudo cp /home/user/file.emerald /usr/bin/etc/etc/etc/etc/etc

That way you are moving (or copying in the example) as the Super User (root) 
(sudo = SuperUser DO)

---

### Post by Lotekx on 2007-11-12
thanks for the help.

The theme is a folder with a bunch of png files in it and an ini file. There is no emerald file. None are selectable in emerald.

---

### Post by willz06jw on 2007-11-12
psst...yea over here where they can't hear us...

They didn't make a emerald file for the theme, so just copy the folder to the theme folder.  In theory this is the wrong way to do it, but the guy who made the theme didn't leave any options.  (That I can tell)[-X

EX:    sudo cp koremin ~/.emerald/theme/

---

### Post by VictorR on 2007-11-12
Usually all emerald themes the user installs from external sources reside in the
~/.emerald/themes/<ThemeName> folders. So if it is not an .emerald file (which is actually just an a packed file) you can copy it to
~/.emerald/themes

You don't have to use sudo for it, just use your favorite file manager.

The different between ~/.emerald/themes and ~/.emerald/theme is that the last contains the currently used theme while the first is the holder of all installed themes.

---

### Post by Lotekx on 2007-11-12
Wow,at first I thought the problem was my own inexperience, but now I realize this really is convoluted.

So I finally got a theme in the emerald theme manager, but now when I click on the theme, nothing changes. Why?Perhaps because in the up-to-date column it says the engine is up to date, 
but next to emerald it says NO(). Is this the reason?

---

### Post by VictorR on 2007-11-12
That's strange. I also have one theme with Emerald NO (up-to-date), but If I select it the windows borders change to that theme.

---

### Post by VictorR on 2007-11-12
I downloaded that KOREMIN theme, copied it to ~/.emerald/themes; it appeared in the list of themes and it had
Engine: YES (0.2)
Emerald: YES (0.2.0).

When I select it it works.

Emerald itself shows 0.3.0-svn.

---

