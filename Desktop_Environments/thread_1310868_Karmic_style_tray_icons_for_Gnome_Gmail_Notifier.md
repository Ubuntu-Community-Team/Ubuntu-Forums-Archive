---
title: "Karmic style tray icons for Gnome Gmail Notifier"
date: 2009-11-02
forum: Desktop Environments
---

### Post by verbme on 2009-11-02
For those who use [Gnome Gmail Notifier]("http://notifier.geekysuavo.org/") but don't like how the icons don't match the new gray Karmic tray icons style: here you go!

Download to a folder on disk, for example the desktop. Then follow these steps:
```
cd ~/Desktop
sudo rename -v 's/\.svg$/\.svg.bak/' /usr/share/gnome-gmail-notifier/*.svg
sudo tar -C /usr/share/gnome-gmail-notifier -xvzf ggn-karmic-style-icons.tar.gz
```

And to revert the changes:
```
sudo rename -vf 's/\.svg.bak$/\.svg/' /usr/share/gnome-gmail-notifier/*.svg.bak
```

---

