---
title: "setting magnet for torrent client"
date: 2013-10-22
forum: Desktop Environments
---

### Post by Tom_ZeCat on 2013-10-22
I'm using Kubuntu 13.10.  The default torrent client for this distro is K-Torrent, which I don't really like.  I much prefer qBittorrent.  I went into KDE's system settings and set qBittorrent as my default client.  So now if I already have a .torrent file on my hard drive I can double click it and qBittorrent comes up, not K-Torrent.  However, turns out setting it as default is not the same thing as the magnet.  Some sites post separate links, a magnet you can click on to automatically start downloading a torrent and another where you can download the torrent file only.  I prefer the latter, but some sites only post a magnet.  If I click on the magnet, K-Torrent always comes up against my wishes, despite qBittorrent being my default.  What's worse, K-Torrent doesn't tell me where it puts the torrent file.  I googled it's location and supposedly it's here: 
~/.kde/share/apps/ktorrent/torX where X is a number

However, I tried using such a file to seed with qBittorrent a torrent I had downloaded with K-Torrent and had no luck.  I've even tried uninstalling K-Torrent, but if I click on a magnet then, Firefox just complains that it can't find my magnet.  I've been looking all through Firefox's settings trying to figure out how to set the magnet for torrents, but I don't find any such setting.  I also have Chrome and Rekonq installed, but no luck with any of these just yet.  

How do I set qBittorrent as my magnet?  I want to use it and just get rid of K-Torrent.

---

### Post by Tom_ZeCat on 2013-10-22
Wouldn't you know it, as soon as I posted this I would stumble across the information.  To help others with the same problem, here's what I found:  

In Firefox, it's Edit ==> Preferences ==> Choose Applications tab

Then scroll down and choose "magnet" and then " use other" and then you have to choose "/usr/bin/qbittorrent".  

All fixed!

---

