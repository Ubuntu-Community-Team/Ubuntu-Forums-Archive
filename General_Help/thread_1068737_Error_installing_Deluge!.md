---
title: "Error installing Deluge!"
date: 2009-02-13
forum: General Help
---

### Post by Schok on 2009-02-13
when i try to install the latest deluge from the website, this shows:

```
sudo dpkg --install deluge-torrent_1.1.2-1_amd64.intrepid.deb
dpkg: considering removing deluge-torrent-common in favour of deluge-torrent ...
dpkg: no, cannot proceed with removal of deluge-torrent-common (--auto-deconfigure will help):
 deluge-torrent depends on deluge-torrent-common (= 0.5.9.3-1)
  deluge-torrent-common is to be removed.
dpkg: regarding deluge-torrent_1.1.2-1_amd64.intrepid.deb containing deluge-torrent:
 deluge-torrent conflicts with deluge-torrent-common
  deluge-torrent-common (version 0.5.9.3-1) is present and installed.
dpkg: error processing deluge-torrent_1.1.2-1_amd64.intrepid.deb (--install):
 conflicting packages - not installing deluge-torrent
Errors were encountered while processing:
 deluge-torrent_1.1.2-1_amd64.intrepid.deb

```

can anyone help?

---

### Post by konqueror7 on 2009-02-13
have you tried uninstalling the deluge-torrent-common? after that you could try then installing deluge, it will still automatically install its dependencies if something is missing...

---

### Post by Schok on 2009-02-13
it works! thanks for helping a noobie ;D

---

