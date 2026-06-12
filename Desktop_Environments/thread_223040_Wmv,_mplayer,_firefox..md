---
title: "Wmv, mplayer, firefox."
date: 2006-07-25
forum: Desktop Environments
---

### Post by boakes on 2006-07-25
Every time I load a WMV file in mplayer it will play the audio just fine, but no video.  Samething goes with the mplayer-mozilla plugin, I get audio, but no video.  The error I get is "Cannot find codec matching selected -vo and video format 0x33564D57."  Now before you say I need to install the w32codecs, they're already installed.  I've reinstalled them several times as well as firefox, as well as mplayer.  I dunno what's going on.  ](*,)

---

### Post by srunni on 2006-07-25
.wmv is a proprietary format. It's not that easy to play it in something other than Windows Media Player. You might want to get WMP10 and wine it to play these files. But I'm sure some of the more experienced people here will have a Linux-native solution.

---

### Post by boakes on 2006-07-25
Wmv plays fine in totem, so it works.  Just not in mplayer.

---

### Post by nix4me on 2006-07-25
wmvs play fine in mplayer. You have to have w32codecs installed.

nix4me

---

### Post by boakes on 2006-07-25
> **nix4me said:**
> wmvs play fine in mplayer. You have to have w32codecs installed.

nix4me

> **boakes said:**
> Now before you say I need to install the w32codecs, they're already installed.    ](*,)
 Next time read please.  Nevermind I fixed the problem, for future reference, if mplayer doesn't play wmv files, just load the windows codecs into /usr/lib/win32 and it'll work just fine.  I had to manually install the w32codecs into that directory.

---

