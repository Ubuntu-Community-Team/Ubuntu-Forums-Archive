---
title: "Default File Manager"
date: 2015-01-14
forum: Desktop Environments
---

### Post by clementchiew on 2015-01-14
So I have installed pcmanfm because my computer is slow. However, every time I open use the "open in file manager" option is the context menu for other application, eg: Deluge, it fires up Nautilus. Can anyone guide to changing the default file manager to pcmanfm? perferably using CLI because I use fluxbox.

---

### Post by konrad6 on 2015-01-14
You can just uninstall Nautilus and it'll have no choice but to use it

sudo apt-get purge nautilus

If you want Nautilus but just not as the default, try reinstalling it and see if pcmanfm gets set as default

---

### Post by deadflowr on 2015-01-14
Don't remove nautilus just yet.
Few things will be removed and you will need to reinstall them if you do.

On top of that, simply removing it won't make the system default to whatever is still installed.
You need to change xdg-mime settings and also make the file manager handle the desktop.

This link is for replacing nautilus with nemo but the principal is the same:
[http://www.fandigital.com/2013/01/set-nemo-default-file-manager-ubuntu.html](http://www.fandigital.com/2013/01/set-nemo-default-file-manager-ubuntu.html)

---

### Post by clementchiew on 2015-01-23
thank you :)

---

### Post by mörgæs on 2015-01-23
If this solves your problem please mark the thread so.

---

