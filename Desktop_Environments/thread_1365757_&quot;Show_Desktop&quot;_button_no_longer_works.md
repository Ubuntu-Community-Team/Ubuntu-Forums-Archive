---
title: "&quot;Show Desktop&quot; button no longer works"
date: 2009-12-27
forum: Desktop Environments
---

### Post by Objekt on 2009-12-27
Earlier today, the "Show Desktop" button on the Plasma dashboard simply stopped working.  You can click all you like, but it doesn't do a damned thing.  What is going on and how do I fix it?  It drives me crazy when stuff stops working for no reason whatsoever.

---

### Post by garryknight on 2009-12-27
Have you tried removing it, then putting it back? No idea if it would work, but it's what I'd try first.

---

### Post by SuperSonic4 on 2009-12-27
That's what I'd try too, especially if there was a recent upgrade.

Also (as user) try ```
kbuildsycoca4
kbuildsycoca4 --noincremental
```

One at a time

---

### Post by Objekt on 2009-12-27
> **garryknight said:**
> Have you tried removing it, then putting it back? No idea if it would work, but it's what I'd try first.

Tried that, but it did nothing.

I also tried reducing the number of desktops to 1.  Same deal.

However, Windows key+d started working the same way it does in Windows: once minimizes everything, again brings everything back.  I'm pretty sure it wasn't doing that before.  I guess I don't need the "Show Desktop" button as much, but I still hate it when stuff stops working for no reason.

---

### Post by hariks0 on 2009-12-28
Try setting Show Desktop Edge Binding to LeftBottom in ccsm. By this you can simply move your mouse to LeftBottom corner and desktop will be shown.

There are some more shortcuts I have set in ccsm. Follow the link in my signature.

---

### Post by Objekt on 2009-12-28
> **hariks0 said:**
> Try setting Show Desktop Edge Binding to LeftBottom in ccsm. By this you can simply move your mouse to LeftBottom corner and desktop will be shown.

There are some more shortcuts I have set in ccsm. Follow the link in my signature.

What is "ccsm?"  I don't have anything called that on my system.

---

### Post by hariks0 on 2009-12-28
It is compizconfig-settings-manager.

---

### Post by Zorael on 2009-12-29
> **hariks0 said:**
> It is compizconfig-settings-manager.
Well, Compiz is sort of irrelevant in a kubuntu thread.

+1 on removing it and readding it; I've had its hotkey break after bigger upgrades (such as to 4.4b1), and removing/readding it always fixed it.

---

### Post by Objekt on 2009-12-29
Negative; removing & readding does nothing.

Lately I've also started having to remove & replace the Klauncher (blue thingy with KDE logo on it).  Sometimes it simply stops responding.

I'm also trying out LXDE instead of KDE.  So far all apps work as they did under KDE, including multimedia.  

That last is a bit of a surprise.  I tried LXDE on my Ubuntu 9.10 install, and found that Flash video simply didn't show up in Firefox.  Hmm.  This has me stumped.

update:

This makes absolutely no sense, but somehow uninstalling Firefox fixed the problem with the "Show Desktop" button.

I've been having some (so I thought) unrelated problems with Firefox, specifically the Firefox Environment Backup Extension, and tried to fix them by reinstalling Firefox.  That problem persists, but suddenly the "Show Desktop" button works again!

I am still having the problem with the K Launcher occasionally refusing to do anything.  I can still fix it by removing it from, then adding it back to the panel, but it's annoying to have to do so.

---

