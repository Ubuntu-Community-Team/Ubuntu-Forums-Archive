---
title: "PCMan File Manager 0.3.2 Beta released"
date: 2006-09-07
forum: Desktop Environments
---

### Post by PCMan on 2006-09-07
Homepage: [http://pcmanfm.sourceforge.net/](http://pcmanfm.sourceforge.net/)
More info:[http://www.gnomefiles.org/app.php?soft_id=1263](http://www.gnomefiles.org/app.php?soft_id=1263)
Project page: [http://sourceforge.net/projects/pcmanfm/](http://sourceforge.net/projects/pcmanfm/)

[IMG]http://pcmanfm.sourceforge.net/screenshot0.png[/IMG]

PCManFM is an extremly fast and lightweight gtk+2 file manager which features tabbed browsing and user-friendly interface.
It's aimed to be a lightweight replacement for nautilus or other heavy file managers.
For full introduction of PCManFM, please go to our homepage.

The latest version 0.3.2 beta has supports for volume management(mount/umount) and displaying icons on desktop.

Here is a screenshot of my current desktop environment:
[http://pcman.sayya.org/pcmanfm/pcmanfm_fbpanel.png](http://pcman.sayya.org/pcmanfm/pcmanfm_fbpanel.png)
The desktop icons are proviede by PCManFM.
The window manager used is IceWM, and the panel at the bottom is a special version of fbpanel modified by me (Adding a much better menu to original fbpanel).
Note: All these 3 programs have no gnome dependencies.

For those who wants to replace nautilus with pcmanfm, I'll write some HOWTO when I have time. The most easy way is uninstalling nautilus, or remove its *.desktop files on the system, and then, run "sudo update-mime-database /usr/share/mime". This might work or might not. If this doesn't work, try "sudo ln -s /usr/bin/pcmanfm /usr/bin/nautils".  <--- This is the worst but effective way.

---

