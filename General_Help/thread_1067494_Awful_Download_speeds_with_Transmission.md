---
title: "Awful Download speeds with Transmission"
date: 2009-02-11
forum: General Help
---

### Post by finlandia420 on 2009-02-11
Odd.  Torrent sites I use on my Windows machine using uTorrent get great download speeds.  Even did side by side tests.  Transmission for some reason forces me to upload crazy amounts compared to my download.  What might have taken hours takes days, and my ratio will be like 5-6.

Played with the setting.  My port is open.  Ran it with/without a router.  Still the same deal.  Should I change clients?

if so, what?

---

### Post by scouser73 on 2009-02-12
I've tried Transmission and I had the same experiences, so I downloaded Deluge which can be found in the repositories and the speeds are excellent now, I'd recommend Deluge over Transmission any day.

---

### Post by solwic on 2009-02-12
I'll be honest with you a lot of people recommend uTorrent ([www.utorrent.com](www.utorrent.com)) but I've had good luck with KTorrent.  

```
 sudo apt-get install ktorrent 
```

Keep in mind that installs a lot of KDE packages if you're not already using KDE.  

I've read arguments that say Transmission is slow because it has no DHT support, which both KTorrent and uTorrent have.  I'm not sure if that's actually why it's so slow or not, but something to keep in mind.  :)

Good luck.  :)

EDIT: Also if you're behind a router, be sure to open up the correct ports (6881 and 4444 in KTorrent, I believe).  I'm no expert with port forwarding, but I know for a fact that DHT won't connect if you have a router blocking those ports.  

:)

---

