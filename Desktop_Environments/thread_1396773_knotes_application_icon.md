---
title: "knotes application icon"
date: 2010-02-02
forum: Desktop Environments
---

### Post by eschoeller on 2010-02-02
Has anyone noticed that the knotes application system tray icon has changed? It used to be a sticky note, now it looks like a slider bar with a vertical LED bar ... almost looks like a volume control!

What's with this? I've tried re-launching the application and it still has this funky icon. Is this just me, or do other people have this problem?

---

### Post by Zorael on 2010-02-03
Hmm. There's an icon cache kept in **~/.kde/cache-hostname/kpc** (obviously, the files beginning with **kde-icon-cache**). Perhaps deleting that would make it "re-read" the icon properly?

---

