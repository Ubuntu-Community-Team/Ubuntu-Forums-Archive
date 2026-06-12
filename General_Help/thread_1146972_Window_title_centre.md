---
title: "Window title centre"
date: 2009-05-03
forum: General Help
---

### Post by Sashin on 2009-05-03
In Ubuntu 9.04, the default human theme has the window title text in the centre. However when I changed to another theme called "Dust" the window titles were shifted to the left. Is there a way to recentre them?

---

### Post by Sashin on 2009-05-03
Bump

---

### Post by CatKiller on 2009-05-03
What window decorator are you using; Metacity or Emerald?

If you're using Emerald, you can change the titlebar settings in System -> Preferences -> Emerald Theme Manager -> Edit Themes -> Titlebar.

If you're using Metacity, I believe the theme is described in an XML file in the metacity sub-directory of whatever theme you're using. If it's a theme you got from gnome-look or somewhere, it'll be in ~/.themes. If it's one of the ones you got through Synaptic (or was installed already) it will be in /usr/share/themes. I don't know which property describes the alignment of the title in the titlebar, but if you compare the files for a theme that has it how you want and your new theme, you should be able to find the change to make.

---

### Post by Sashin on 2009-05-03
It's a GTK2/metacity theme that was already installed.

I found the file but I'm not sure what exactly to modify...

---

### Post by Sashin on 2009-05-03
Bump again

---

### Post by CatKiller on 2009-05-03
It's not considered polite to bump a post more than once a day.

> **Sashin said:**
> It's a GTK2/metacity theme that was already installed.

I found the file but I'm not sure what exactly to modify...

Nor am I. You'll have to compare the two approaches to see what to change, or read up on Metacity theming in general.

---

### Post by Sashin on 2009-05-03
Fair enough, it would be nice if there was a GUI for this...

---

### Post by CatKiller on 2009-05-03
> **Sashin said:**
> Fair enough, it would be nice if there was a GUI for this...

Yes it would. However, most people aren't really interested in creating their own themes, so there isn't really that much demand for a GUI tool to be installed by default. And there is a GUI for the newer Emerald way of theming.

There's a GUI tool for testing Metacity-themes-in-progress, called metacity-theme-viewer. It's probably in the repositories. [This page]("http://developer.gnome.org/doc/tutorials/metacity/metacity-themes.html") might help you get started on how to change Metacity themes to be more how you want them.

---

