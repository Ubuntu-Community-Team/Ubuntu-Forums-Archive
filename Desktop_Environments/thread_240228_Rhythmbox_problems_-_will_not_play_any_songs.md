---
title: "Rhythmbox problems - will not play any songs"
date: 2006-08-20
forum: Desktop Environments
---

### Post by phantasmagoriana on 2006-08-20
Hi,

I upgraded from Breezy to Dapper this morning, and now Rhythmbox Music Player doesn't seem to work (it was working fine with Breezy).

All my music is stored on an NTFS partition (mixture of .mp3 and .m4a - I've checked that I have the right plugins installed). When I try to open Rhythmbox it loads the correct files, but as soon as I try to play any of them it just scrolls down the list rapidly and doesn't actually play anything. It does put little red "stop" signs by some of the track names though.

Can anyone help? I could just use XMMS, which is working fine, but I prefer Rhythmbox's interface...](*,)

---

### Post by sapo on 2006-08-20
```
sudo apt-get install gstreamer0.10-plugins.*
```

It happens becausa breezy used gstreamer0.08 and Dapper uses 0.10, just install the gstreamer plugins and be happy :)

---

### Post by phantasmagoriana on 2006-08-20
> **sapo said:**
> ```
sudo apt-get install gstreamer0.10-plugins.*
```

It happens becausa breezy used gstreamer0.08 and Dapper uses 0.10, just install the gstreamer plugins and be happy :)

Aha, didn't realise that. Fixed now - thank you! :)

---

