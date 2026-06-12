---
title: "Title Bar Transparency"
date: 2007-11-05
forum: Desktop Effects &amp; Customization
---

### Post by picopir8 on 2007-11-05
Is there a menu in compiz settings manager (or anywhere else) for adjusting the active window title bar transparency?  I found an option to make the entire window transparent, but I only want the title bar to be transparent.

I am looking for something similar to "Active Window Opacity" slide that was in gnome_compiz_manager

---

### Post by psyopper on 2007-11-05
The standard theme engine in Ubuntu doesn't support title bar / window frame transparency. You need to install the Emerald Theme Engine to get this effect. Unfortunately I'm not too keen on installing Emerald in Gutsy...

---

### Post by Forlong on 2007-11-05
```
sudo apt-get install emerald
```
After this, there will be the Emerald Theme Manager in System &#8594; Preferences where you can set the theme you are using any way you want.

There are many themes available for Emerald on sites like gnome-look

---

### Post by smartboyathome on 2007-11-05
Also, you may want to install [this package]("http://mirrors.kernel.org/ubuntu/pool/universe/e/emerald-themes/emerald-themes_0.2.1-0ubuntu1_all.deb") from ubuntu which installs some starter Emerald themes for you to enjoy. :)

---

### Post by gsiliceo on 2008-04-28
I found the option you are looking for, you'll need gconf-editor, just open it: its in the system tools menu(you might need to enable it using the menu editor) or just type 
> gconfg-editor
In the terminal.
Then go to apps/gwd,and there you will find a few useful options among them the one you want to change. I don't know why there is no gui to do this easier, but whatever is not that hard.

---

