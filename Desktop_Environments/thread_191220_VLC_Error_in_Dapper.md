---
title: "VLC Error in Dapper"
date: 2006-06-07
forum: Desktop Environments
---

### Post by j-strap2 on 2006-06-07
I can install VLC OK, but I keep getting these errors when I try to run it:

```

VLC media player 0.8.4 Janus
[00000270] main dialogs provider error: no dialogs provider module matched "any"
[00000267] skins2 interface error: No suitable dialogs provider found (hint: compile the wxWidgets plugin, and make sure it is loaded properly)
[00000267] skins2 interface: skin: VLC OSX Interface  author: BigBen

```

According to the VLC site, this is something to do with wxwindows, but I have this installed. Anyone else getting the same problem?

---

### Post by j-strap2 on 2006-06-08
Something must have got corrupted when I tried to run VLC for the first time. I deleted the .vlc directory, and the problem was cured.

---

