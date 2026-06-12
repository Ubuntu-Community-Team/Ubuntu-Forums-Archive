---
title: "Installing icon themes."
date: 2005-12-21
forum: Desktop Environments
---

### Post by equal on 2005-12-21
Hi, I just switched over to my KDE desktop from GNOME, and I found some sweet icon themes on kde-look.org, but I can't figure out how to install them properly. Help?

For reference sake, I'm trying to install [this one]("http://www.kde-look.org/content/show.php?content=8520").

---

### Post by Juippisi on 2005-12-21
Download it to your home directory, extract it, move the directory under ~/.icons and open K Control Center. There, go to "Appereance & Styles -> Icons" and select your new icon-theme.

For example:
cd ~
wget [http://icon.theme.org/icons.tar.gz](http://icon.theme.org/icons.tar.gz)
tar -xzvf icons.tar.gz
mv icons .icons
kcontrol

Hope this helps!

---

### Post by equal on 2005-12-21
Turns out it's even easier than that. You go into Appereance & Styles -> Icons, and then click Install New Theme. You can actually enter the URL of the theme file and it'll download and install it for you. I was way too tired last night when working on this!

---

### Post by Juippisi on 2005-12-22
Damn that KDE makes your life easier ;-).

---

