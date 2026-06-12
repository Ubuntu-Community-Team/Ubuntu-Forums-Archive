---
title: "New version of Wallpapoz"
date: 2005-12-07
forum: Desktop Environments
---

### Post by Bob Morane on 2005-12-07
I just received news from Akbar regarding Wallpapoz. For those who haven't heard of it before, it's a little deamon for gnome alowing users to have different desktop backgrounds on different workspaces, and/or to periodically change the DB. It crashed with a segmentation fault on breezy previously. Akbar now uses python rahter then c++ for the source and it Wallpapoz should work on ubuntu.

[QUOTE="Akbar"]

This is the latest official Wallpapoz release available.
wallpapoz-0.3.tar.bz2

I decided to convert c++ source to python source because c++ source has a difficult-to-fix bug. C++ version of Wallpapoz runs fine in Fedora Core 4, but gets segmentation fault ( for specifically the daemon get it ) in Ubuntu Breezy Badger. So I decided to convert it to python source. Now it runs fine in Ubuntu Breezy Badger. I add little modification into wallpapoz gui when converting to python source.

Wallpapoz needs pygtk and python-glade2. Tested with 2.8 version but I think it should work with 2.6 version.[/QUOTE]

You can download the latest (python) version there :
[http://wallpapoz.sourceforge.net/download.html]("http://wallpapoz.sourceforge.net/download.html")

---

### Post by Cordate on 2005-12-10
Very cool :) I couldn't get the previous version to work under Hoary but now with this new python/Breezy combination it runs fine.

---

