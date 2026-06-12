---
title: "Installing themes?"
date: 2006-08-29
forum: Desktop Environments
---

### Post by 1oki on 2006-08-29
Ok, this maybe a n00b question... but how the heck does one install themes from places like gnome-look.org? I tried downloading their ubuntu packages and installing them wth dpkg but i cant find it anywhere! 

L

---

### Post by ebash on 2006-08-29
To install a theme simple open the Theme Preferences window, go into the Main Menu > System > Preferences > Themes. Once you have this window open you can drag-and-drop your theme there.

If you are using firefox you don't even need to download the theme you can simply drag and drop the URL of the theme package and it will be installed automatically.

---

### Post by 1oki on 2006-08-29
I've tried that... What does the file format have to be for the theme manager, and where can I input the URL from firefox? 

I have tried the theme manager multiple times, I have even tried the ubuntu packages  (.deb) to install a theme... When I try to install the theme w/ the manager, I usualy get an invalid file format. with the .deb I cant locate the theme in the manager! So im alittle lost... Where do you guys get your theme's? I can change it to another ubuntu integrated theme... but i want a custom one :)

---

### Post by ebash on 2006-08-29
You can download themes from various sites some of the most famous are 
[http://art.gnome.org/]("http://art.gnome.org/")
and
[http://www.gnome-look.org/?content=19527]("http://www.gnome-look.org/?content=19527")

There are four different kinds of themes that can be downloaded. Themes for Metacity, the window manager, these themes will only change the frames of windows. Gtk themes, this will change how buttons, scrollbars, text and any visual widget is displayed, icon themes and and finally a meta theme that's groups together the three kinds of themes (metacity, gtk and icons).

Normally, all themes are distributed in a tar.gz format.

To install a theme you can download the tar.gz file and then feed it to the 'Theme' manager program. Or you can just drag-and-drop the URL of the theme into the 'Theme' manager program.

Example
-------
Go to arg.gnome.org at the right you should see the navigation menu look for 'Desktop Themes' > 'Application' (This section holds the GTK themes).

Now choose a theme that pleases you and click on it you should be presented with a description of the theme. That very same page should have a blue/grey box with the title 'Download'. That's the link that you should either download or drag-and-drop into the 'Theme' application.

If this doesn't work, you might be facing a strange bug. But all hope is not lost. You can install the theme by hand very easily. You can install a theme in your home acocunt. All that you need to do is to untar the theme in the folder ```
.themes
``` that's in your home account. The 'Theme' application should see the new theme.

Take note that if you install a new theme that's not a metatheme you will need to click the 'Theme details' button in the 'Theme' application and choose that theme there.

---

