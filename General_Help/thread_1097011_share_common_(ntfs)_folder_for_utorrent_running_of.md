---
title: "share common (ntfs) folder for utorrent running off win/linux ?"
date: 2009-03-15
forum: General Help
---

### Post by vikrant_me on 2009-03-15
Is it possible to share a common folder to download torrents using utorrent running off windows as well as linux and resume a download started off one OS from another OS like resume an incomplete download from a windows boot after booting into linux ?

---

### Post by vikrant_me on 2009-03-15
This seems to have been answered here already :) however i would not like to run utorrent in wine in ubuntu and now need to look for a torrent app that works both in windows and ubuntu 

[http://ubuntuforums.org/archive/index.php/t-494432.html](http://ubuntuforums.org/archive/index.php/t-494432.html)

---

### Post by mrsteveman1 on 2009-03-15
I've tried doing that before, it's a bad idea :)

Vuze is entirely cross platform but i don't like it, however any of the common Linux torrent clients should work on any platform with Qt or GTK+ support, which would be windows of course. Now whether they provide Windows packages and whether things would actually work the way you want i don't know.

---

### Post by lovinglinux on 2009-03-15
I don't think this is a good idea, but you could use Deluge, which is an excellent torrent app (better than uTorrent IMO). Deluge has Ubuntu and Windows versions.

Make sure you configure Deluge to save the downloaded files and copy the torrents to a ntfs drive. Deluge uses a file with ".torrent.fastresume" extension to control the status of the download, so if you want to resume the download from both OS you have to make sure they share the same torrent directory.

You can download Deluge from [http://dev.deluge-torrent.org/wiki/Download](http://dev.deluge-torrent.org/wiki/Download)

---

