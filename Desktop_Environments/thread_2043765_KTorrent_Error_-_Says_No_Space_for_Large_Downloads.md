---
title: "KTorrent Error - Says No Space for Large Downloads"
date: 2012-08-17
forum: Desktop Environments
---

### Post by uv_goth on 2012-08-17
Error only appears if downloading a large magnet link/download. It is fine for normal sized files.

It says "Stopped. No space left on device" when I try to start the download. There's 212GB of space left!

I suppose I could remove KTorrent and associated files and try a fresh install of it but that might be a bit overkill... 

(Kubuntu 12.04, KTorrent 4.1.3)

---

### Post by uv_goth on 2012-08-17
So this is due to the old version of KTorrent saving magnet links at /home/.kde/share/apps/kio_magnet and my /home is a separate partition which is much smaller.

---

