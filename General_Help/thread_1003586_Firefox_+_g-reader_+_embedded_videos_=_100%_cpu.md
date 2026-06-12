---
title: "Firefox + g-reader + embedded videos = 100% cpu"
date: 2008-12-06
forum: General Help
---

### Post by thk on 2008-12-06
I've noticed recently that firefox (3) become unusable after browsing google reader in "expanded" view. When I page past news items with embedded video clips (youtube mostly), the cpu load goes to 100% and stays. If I continue, things slow to a crawl. It is as if firefox is actually playing the videos in the background. Sometimes I notice that the black square for the video clips does not fully refresh, but is left hanging at the bottom of the browser window (covering the next news item). Anyone have a fix?

---

### Post by thk on 2008-12-08
Known bug in adobe's flash plugin.

Solved by:

```

sudo apt-get remove flashplugin-nonfree
sudo apt-get install adobe-flashplugin

```

Must be pulling in a different version.

---

