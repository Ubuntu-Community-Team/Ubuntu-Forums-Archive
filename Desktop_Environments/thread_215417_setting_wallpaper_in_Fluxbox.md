---
title: "setting wallpaper in Fluxbox"
date: 2006-07-13
forum: Desktop Environments
---

### Post by RavenOfOdin on 2006-07-13
Downloaded this. . .installed it. . .and I just can't seem to get the wallpapers working.  I've tried other solutions on this forum such as using fbsetbg -l/-C, using other applications to pop up wallpaper (such as Feh), but its not helping.

More appropriately, Feh or any other app just doesn't let the wallpaper stay up - the default of the Fluxbox theme I'm using overrides it as soon as startup proper is complete. 

I've tried putting the line "rootCommand:   Esetroot -center /path/to/file" in my theme file but it doesn't even let the wallpaper pop up at all.

Any ideas?

---

### Post by taurus on 2006-07-13
Here is what I have in my ~/.fluxbox/startup...
```

fbsetbg -f /home/taurus/pictures/debian.jpg &

```

---

