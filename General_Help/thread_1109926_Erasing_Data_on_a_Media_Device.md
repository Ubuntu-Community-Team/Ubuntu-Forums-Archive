---
title: "Erasing Data on a Media Device?"
date: 2009-03-29
forum: General Help
---

### Post by kiisu on 2009-03-29
hi,
I use my old mobile Nokia phone primarily as a backup mp3 player. A few days I ago I hooked it up, as usual by USB, and put some new music on it. Nothing out of the ordinary. But just now I hooked it up again, the device mounted no problem, but it shows up as totally blank, so I can't delete any of the files.
If I right-click on the device and look at properties, it shows up as 100% full so I can't put any music on it. I need a way to delete the files off of it ... Also, I checked on my gf's mac and the same thing happens so it's not just a problem of Ubuntu not seeing the files.
is there a terminal command I could use to just delete these files?
thanks

---

### Post by dcstar on 2009-03-30
> **kiisu said:**
> hi,
I use my old mobile Nokia phone primarily as a backup mp3 player. A few days I ago I hooked it up, as usual by USB, and put some new music on it. Nothing out of the ordinary. But just now I hooked it up again, the device mounted no problem, but it shows up as totally blank, so I can't delete any of the files.
If I right-click on the device and look at properties, it shows up as 100% full so I can't put any music on it. I need a way to delete the files off of it ... Also, I checked on my gf's mac and the same thing happens so it's not just a problem of Ubuntu not seeing the files.
is there a terminal command I could use to just delete these files?
thanks

Do an fsck on it (after unmounting) - either on the command line or use the Partition Manager to check it.

---

