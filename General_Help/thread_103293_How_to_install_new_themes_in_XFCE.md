---
title: "How to install new themes in XFCE?"
date: 2005-12-13
forum: General Help
---

### Post by Gadren on 2005-12-13
It's odd -- while I enjoy Xubuntu greatly, I don't even know how to add themes to it, and I haven't been able to find any good info on it.  Can anyone help?

---

### Post by kairu0 on 2005-12-13
There is a probably a "GUI" way to do it, but I unpack them into my ~/.themes directory.

---

### Post by landotter on 2005-12-13
You can use the gnome-theme-manager app to add gtk themes, as xfce uses the same ones as gnome. Alternately, make a directory /home/username/.themes and drop the uncompressed theme archive in there.

Don't know how to add xfwm themes, but enough are installed by default to make most folks happy.

---

### Post by matthew on 2005-12-13
I have never done this, so I'm just quoting from the first link.

> **XFCE**    
XFCE themes are managed through the xfskin program. After you've downloaded a theme, type "xfskin &", navigate to the "file --> add" menu item, point the file selector to the tarball, and click "install". xfskin can also be used to create and delete themes. 
 
[http://freshmeat.net/articles/view/465/#xfce-use]("http://freshmeat.net/articles/view/465/#xfce-use")

This is also likely to interest you:  [http://xfce-look.org/]("http://xfce-look.org/")

---

### Post by tawie on 2005-12-13
it's very easy, just untar the theme to /usr/share/themes directory.
and from the xfce settings to select 'window manager ' and 'user interface' to change the themes.

---

### Post by Gadren on 2005-12-13
Odd.  I've created a ~/.themes directory and untared it in there, as well as untaring it into /usr/share/themes, but they don't appear on the settings list.  And xfskin doesn't exist, according to bash.

Do I have to refresh the XFCE desktop or something?  And how do I do that?

---

### Post by dj_flx on 2006-01-07
[QUOTE=Gadren]Odd.  I've created a ~/.themes directory and untared it in there, as well as untaring it into /usr/share/themes, but they don't appear on the settings list.  And xfskin doesn't exist, according to bash.

Do I have to refresh the XFCE desktop or something?  And how do I do that?[/QUOTE]

I have exactly the same problem. I've tried both ways as well; for example, untarring [this]("http://www.xfce-look.org/content/show.php?content=23142") file into both directories, tried restarting, etc.

Any particular reason that file shouldn't show up in my list? I also seem to lack xfskin, and it doesn't show up in Synaptic.

---

### Post by theadventuresofanidealist on 2007-04-20
same problem here but only with xfwm4 themes :(

---

