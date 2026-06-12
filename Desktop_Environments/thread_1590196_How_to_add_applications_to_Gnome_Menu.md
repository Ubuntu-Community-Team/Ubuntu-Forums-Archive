---
title: "How to add applications to Gnome Menu"
date: 2010-10-07
forum: Desktop Environments
---

### Post by aldav on 2010-10-07
Hello. I'm developing a mono application and I want to make a script so I can create a shortcut in the Gnome Menu. How can I make that?

Thanks

---

### Post by gzarkadas on 2010-10-07
You just have to create your menu-item as a .desktop file with the appropriate content and from your install script, copy it to /usr/share/applications and set its permissions with chmod 644 (both as root).

Use the files inside /usr/share/applications as templates to make your own. There are also, for reference:

1. A [guide in the tutorials section]("http://ubuntuforums.org/showthread.php?t=36479") of the forum that explains the menu system; though for sub-menus it is useful as a starting point.

2. [The Desktop Entry Specification]("http://standards.freedesktop.org/desktop-entry-spec/latest/").

3. [The XDG base directory specification]("http://standards.freedesktop.org/basedir-spec/latest/index.html").

---

