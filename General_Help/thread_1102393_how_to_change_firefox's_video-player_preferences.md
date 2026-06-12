---
title: "how to change firefox's video-player preferences"
date: 2009-03-21
forum: General Help
---

### Post by shamimkhaliq on 2009-03-21
i installed an old favourite media player of mine, vlc, and its firefox plugin. unfortunately, online streaming videos didn't find vlc even after i uninstalled other media plugins. i read:

"VLC Firefox Default?
you should check what program firefox might be looking for when encountering different codecs. After installing restricted package and the vlc plugin;
In FF, check: Edit -> Preference -> Application (tab)
Change each file to use vlc plugin."

but when i click "use other.." it asks me to browse for the media player. where are programs in the file system of ubuntu hardy?

---

### Post by Steve1961 on 2009-03-21
Install mozilla-mplayer and uninstall the vlc plugin and totem mozilla.

Note: you'll also need the package w32codecs from the medibuntu repository.

---

### Post by zika on 2009-03-21
> **shamimkhaliq said:**
> flash didn't work, kept sticking, even after i uninstalled other flash players and installed adobe's. so i installed an old favourite media player of mine, vlc, and its firefox plugin. unfortunately, online streaming videos didn't find vlc even after i uninstalled other media plugins. i read:

"VLC Firefox Default?
you should check what program firefox might be looking for when encountering different codecs. After installing restricted package and the vlc plugin;
In FF, check: Edit -> Preference -> Application (tab)
Change each file to use vlc plugin." in an archived post

but when i click "use other.." it asks me to browse for the media player. where are programs in the file system of ubuntu hardy?
/usr/bin/vlc

---

### Post by shamimkhaliq on 2009-03-21
> **zika said:**
> /usr/bin/vlc

thanks so much.

---

