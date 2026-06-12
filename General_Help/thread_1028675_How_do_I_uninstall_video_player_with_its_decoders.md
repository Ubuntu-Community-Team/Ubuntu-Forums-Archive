---
title: "How do I uninstall video player with its decoders?"
date: 2009-01-02
forum: General Help
---

### Post by gMinuses on 2009-01-02
Say, I installed MPlayer through Synaptic Package Manager, and it was shipped with some decoder. Later, I want to uninstall it. So how do I uninstall these decoders automatically as well? I don't remember their names and unable to find them in the list.

---

### Post by adult swim on 2009-01-02
just search for mplayer in synaptic package manager and then click it and select "mark for complete removal"

---

### Post by gMinuses on 2009-01-02
"just search for mplayer" seems to result in removing the main program only. The first time I installed MPlayer, I was prompted with these decoders, but after unstalling it and restalling it, no decoder showed up, from which I conclude that they are no removed.

---

### Post by adult swim on 2009-01-02
try from terminal
```
sudo apt-get remove --purge mplayer

sudo apt-get autoremove
``` the first will get rid of the player and the second will clean up all of those codecs and things left over.

---

### Post by gMinuses on 2009-01-02
Uninstalled lots of stuff. Thanks!

---

