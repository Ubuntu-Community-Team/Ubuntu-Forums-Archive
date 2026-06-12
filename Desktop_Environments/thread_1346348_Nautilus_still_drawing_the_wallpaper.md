---
title: "Nautilus still drawing the wallpaper?"
date: 2009-12-05
forum: Desktop Environments
---

### Post by carlinuxlearner on 2009-12-05
I'm trying to set my wallpaper to be a screen saver (via this command: "/usr/lib/xscreensaver/glmatrix -root").

However, **after** unchecking "show-desktop" (in gconf-editor /apps/nautilus/preferences/show_desktop) it still displays the wallpaper I had before, and the command to set the screensaver as my wallpaper does nothing (at least, nothing that I can see).

Now, a few things you might like to know:
1. I'm running compiz-fusion.
2. If I set compiz to draw the wallpapers, it does. **However** I happen to have a transparent image as my top menu bar, and through the image, you can still see the old wallpaper (drawn by nautilus), so clearly, something is still drawing that image even though compiz is puting an image over it.

So, what is still drawing that wallpaper on my desktop even though I turned it off? And how can I fix it?

---

### Post by carlinuxlearner on 2009-12-18
Um... ***bump***. 

(come on folks, surely I'm not the only one)

---

### Post by HHristov on 2010-01-08
I have a similar problem. I have multiple workspaces and I've set different wallpapers on each one with ccsm. When i set the top and bottom panels' transparency to 0 i see the wallpaper set from nautilus. Is there a way to fix this?

---

### Post by wlourf on 2010-01-08
Did you try to run nautilus with the no-desktop option :
```
nautilus --no-desktop
```

---

### Post by HHristov on 2010-01-09
> **wlourf said:**
> Did you try to run nautilus with the no-desktop option :
```
nautilus --no-desktop
```

I just tried that and nothing happened except that one of my desklets and the desktop icons disappeared. Checking the show desktop option through gconf-editor>apps>nautilus>preferences didn't return them.

Edit: I managed to return my desktop icons but the InfoPanel desklet is still missing. Is there a command that can undo the nautilus --no-desktop command?

---

