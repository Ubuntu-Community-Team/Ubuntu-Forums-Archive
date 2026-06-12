---
title: "Gnome always on top - how to set media player to auto open as always on top"
date: 2007-10-05
forum: Desktop Environments
---

### Post by desertboy on 2007-10-05
I want to set mplayer (or vlc) to always be on top I know any gnome window can be set to always on top but I want this turned on as default when I open Mplayer.

Thanks

---

### Post by desertboy on 2007-10-06
Flump

---

### Post by desertboy on 2007-10-08
Bump

---

### Post by desertboy on 2007-10-10
Bump I'm guessing n one knows, or maybe it's impossible.

---

### Post by Namtabmai on 2007-10-10
Unfortunately as far as I know, the default Gnome window manager metacity doesn't support stuff like this. But if you have Compiz install you can get this to do what you want. Open up the compiz settings and enable the "Window Rules" module. In the "Above" box put
```

class=Totem || class=MPlayer || class=VLC || title=VLC media player

```
This should cover you for some of the most popular media players, but I found that VLC didn't really play that nicely with this setting enabled, but with VLC if you go to Settings->Preferences under the video tab there is "Always on top", check this an hopefully that should fix things for you.

---

### Post by Wolki on 2007-10-10
You can also do it with metacity ()GNOME's default window manager) if you use devilspie. I wrote a guide for it a long time ago and configuration has changed since then, which I only cover briefly, but it might still explain the concept. See [http://ubuntuforums.org/showthread.php?t=75749](http://ubuntuforums.org/showthread.php?t=75749)

---

