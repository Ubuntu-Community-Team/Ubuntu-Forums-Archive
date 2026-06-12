---
title: "WoW changing resolution issue"
date: 2007-06-01
forum: Gaming &amp; Leisure
---

### Post by Wallakoala on 2007-06-01
just installed WoW, and I know you can't normally change the resolution ingame, so I edited the Config.wtf file located in the WTF folder. I really want it to be 1080x1024, but for some reason whenever I start up the game, it reverts what I put in the config.wtf back to 800x600. Please help.

---

### Post by hikaricore on 2007-06-01
shouldn't it be 1280x1024?  if not it may be an issue with widescreen resolutions, make sure your xorg.conf file supports said resolution or the video mode will not change properly.

---

### Post by ShadowFlar3 on 2007-06-01
The game attempts to auto-detect "correct" settings. SET hwdetect "0" in config.wtf should fix it.

---

### Post by Wallakoala on 2007-06-02
> **ShadowFlar3 said:**
> The game attempts to auto-detect "correct" settings. SET hwdetect "0" in config.wtf should fix it.

ahh thank you so much! that worked.  But now i have another related issue....I like to change the UI scale to .64 but for some reason whenever I change it in the Config.wtf, it doesn't show the change in the game. The UI scale always remains at 1, no matter what I put in the Config.wtf

---

### Post by pianoboy3333 on 2007-06-03
that's weird, i've never heard of that.

---

