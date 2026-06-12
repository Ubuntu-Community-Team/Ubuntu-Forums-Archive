---
title: "wallpaper settings broken after Multi Backgrounds Daemon"
date: 2008-09-15
forum: Desktop Environments
---

### Post by boddhisatva on 2008-09-15
I've tried a little program called Multi Backgrounds Daemon 0.1.2, which offered to set a different wallpaper for each workspace/viewport. After running it the background turned a uniform colour and I can't set any wallpaper on any workspace. Even after stopping the program, uninstalling it, and restarting the system. I also tried switching off Compiz. The ability to set wallpapers is gone, only the colour changes. Any idea what this program has screwed up and how to fix it? I'm running Hardy.

---

### Post by boddhisatva on 2008-09-16
OK, I've fixed it. I had to tick the draw_background variable in gconf-editor, which had apparently got unticked by the Daemon (or, should I say, a demon?). God (Daemon) knows why.

---

