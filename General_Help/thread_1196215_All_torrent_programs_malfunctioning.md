---
title: "All torrent programs malfunctioning"
date: 2009-06-24
forum: General Help
---

### Post by ed-koala on 2009-06-24
I searched but did not find an answer to this, so I need some help.

Currently, Deluge and Transmission will not download ANY torrents (even the official Ubuntu one).  I use Deluge mostly, so hopefully we can troubleshoot using it. That said, here is the details:

Port opened properly - checked router and performed web test
UPnP enabled
Encryption enabled (both ways)
No plugins installed
No firewall security

Deluge will start a torrent the first time, then soon after the torrent stops with a "permission denied" error. Afterward the torrent just will not start (stays grey).

If any other info is needed, let me know. I'm not a newbie at this, and it all worked fine not long ago, but obviously something changed.  Need to get this working!

---

### Post by michy99 on 2009-06-24
Where are you saving the file to? Do you have write permission for that directory?

---

### Post by ed-koala on 2009-06-24
I feel like an idiot. Yes, I had permission for the files, but even though I changed the download directory, it didn't change the path of existing torrents. Had to delete torrent, set download path (again) and re-acquire.

Seems to be working atm.  Thanks for the suggestion, it pointed me in the right direction.

---

