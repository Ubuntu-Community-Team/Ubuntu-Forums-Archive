---
title: "KTorrent keeps &quot;complaining&quot; about deleted torrents"
date: 2006-09-08
forum: Desktop Environments
---

### Post by mibadt on 2006-09-08
Hi,
I use KTorrent (2.0.2) in Kubuntu (KDE 3.5.4).
Long ago, I've removed several torrents which weren't active and weren't (fully) downloaded.  Ever since, whenever I open KTorrent, I get multiple error messages (something like error: missing or bad torrent) which probably refer to those removed torrents (afterwards KTorrent opens and works).

These old torrent do **not** appear in KTorrents window.

PLease advise how to stop this annoyance?

TIA

---

### Post by Jucato on 2006-09-08
you can check in ~/.kde/share/apps/ktorrent if there are remnant tor# folders. These folders contain the information for those torrents you downloaded. Just be careful you don't delete the folders of active/working torrent that you are currently downloading.

---

### Post by mibadt on 2006-09-08
Bless you,
That ineed solved the problem  :D

---

