---
title: "How to install BitTorrent"
date: 2006-07-05
forum: Desktop Environments
---

### Post by dolby on 2006-07-05
i am trying to install the official bittorrent client on xubuntu, but cant seem to do so. i downloaded the deb file from the site but it doesnt seem to work, as well as the instructions [here](http://ubuntuforums.org/showpost.php?p=433965&postcount=2) didnt help much either.

---

### Post by taurus on 2006-07-05
Make sure you have both universe and multiverse in your /etc/apt/sources.list.  Then,
```

sudo apt-get update
sudo apt-get install bittorrent

```

---

### Post by dolby on 2006-07-05
i was actually refering to the latest bittorent version. the one in the repos is significantly outdated i reckon

---

### Post by taurus on 2006-07-05
Well, if you can tell me exactly where you downloaded and which version, perhaps I can give you some hints on how to install it...

---

### Post by dolby on 2006-07-05
i downloaded this file : [http://download.bittorrent.com/dl/BitTorrent-4.20.2.tar.gz](http://download.bittorrent.com/dl/BitTorrent-4.20.2.tar.gz). checked if i have the packages suggested [here](http://ubuntuforums.org/showpost.php?p=433965&postcount=2) and tried to open a torrent with the bittorrent.py file but it didnt work.

---

### Post by taurus on 2006-07-05
You need to install all those programs as described in INSTALL.unix.txt first:

Install Python, version 2.3 or later. (2.4 recommended)
Install wxWidgets, version 2.6 or later, in the Unicode flavor.
Install wxPython, version 2.6 or later, in the Unicode flavor.
Install GTK, version 2.6 or later.
Install Twisted, version 2 or later.
Install PyCrypto, version 2 or later.
Install Psyco.
Install Zope.

So, you may want to use synaptic and search and install those packages first before you can install and run the latest version of bittorrent.  And don't forget to remove the older version if you have it on your system...

---

### Post by flaming_monkey on 2006-07-05
[QUOTE=dolby]i am trying to install the official bittorrent client on xubuntu, but cant seem to do so. i downloaded the deb file from the site but it doesnt seem to work, as well as the instructions [here](http://ubuntuforums.org/showpost.php?p=433965&postcount=2) didnt help much either.[/QUOTE]

I've tried the latest Bittorrent Client and there isn't much improvement. I'd stick to [Azureus](http://azureus.sourceforge.net/) + Java 1.5 or use [utorrent](http://www.utorrent.com/) under Wine, as these both seem to connect and download a lot better IMHO.

---

### Post by dolby on 2006-07-06
i think i'll just stick to bittornado for the time being

---

