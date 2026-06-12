---
title: "nautilus hangs when browsing &quot;big&quot; autofs folders"
date: 2006-08-27
forum: Desktop Environments
---

### Post by mosestruong on 2006-08-27
I have a remote file server containing many photos which I use autofs to mount from my laptop.

Everything is fine with folders that don't contain many photos. However, when there's a folder with many photos in it, Nautilus will hang after loading a few thumbnails. And when it occurs and I try to restart autofs, it says it couldn't stop autofs...

Are there any way to overcome this problem? Thanks

---

### Post by stdragon on 2006-08-28
I think it's just trying to create thumbnails for the files. It hasn't really frozen. If you wait a while it should come back. Otherwise you can disable thumbnails in nautilus's options. To do that, open nautilus in a different directory and go to Edit -> Preferences -> Preview and change the "Show Thumbnails" option to Never.

Good luck!

---

