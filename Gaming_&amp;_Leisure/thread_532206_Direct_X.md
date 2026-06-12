---
title: "Direct X"
date: 2007-08-22
forum: Gaming &amp; Leisure
---

### Post by Person753951 on 2007-08-22
Hi,
im trying 2 install NFS carbon using WINE but its saying that it wont work without DirectX.
how can i get directx 4 wine?

---

### Post by splintercellguy on 2007-08-22
If you run the app in the Terminal, what output does it produce?

---

### Post by cogadh on 2007-08-22
Wine already has DirectX libraries built in and trying to install DX will break those libraries, meaning no games will work in Wine. 

However, NFS: Carbon has a "Garbage" rating on Wine's AppDB and may not work at all. It does say that you will need to add overrides for d3dx9_30.dll, fusion.dll and MSVCR.dll to get past the initial errors, but it still crashes after that. The most recent test was done with Wine 0.9.31, so it may be worth trying with the latest Wine (0.9.43). There have been significant DX updates since version 0.9.31.
[http://appdb.winehq.org/appview.php?iVersionId=6224](http://appdb.winehq.org/appview.php?iVersionId=6224)

---

