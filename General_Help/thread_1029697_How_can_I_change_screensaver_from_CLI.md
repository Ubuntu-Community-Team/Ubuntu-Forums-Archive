---
title: "How can I change screensaver from CLI"
date: 2009-01-03
forum: General Help
---

### Post by timjohn7 on 2009-01-03
I changed the screensaver from Blank Screen to Random and something broke ... I can no longer log in.  I either want to disable the screensaver or switch it back  to blank screen so that I can function!

---

### Post by fr0sty on 2009-01-03
Try rebooting your computer. When ubuntu tries to load, you might get the option of booting up in safe graphics mode. If you get this then you can get back into ubuntu and then change your screensaver back to blank. Im guessing it could have to do with any of the 3d GL screensavers that use graphics card acceleration. hopefully this is somewhat helpful.

---

### Post by stderr on 2009-01-03
Should be easy. I don't have kubuntu, so you'll have to locate the correct gconf key.

For me under Ubuntu (gnome), I'd just do:

```
gconftool-2 --set /desktop/gnome/background/picture_filename --type string "/path/to/image/image.jpg" 

```

Clearly, your path won't be /desktop/**gnome**/...

edit: LOL entirely ignore my post. I must be nuts :) gconf does indeed stand for **Gnome** CONFiguration...

I don't know where KDE stores the setting.

edit2: Found this, may be worth a go, although obviously I can't test it this end. I wasn't aware of this, but it seems KDE uses dcop for configurations, which I'm guessing from this isn't so dissimilar from gnome's gconf. Although, from this, it doesn't appear as though it uses a registry-style setup.

```
dcop kdesktop KBackgroundIface setWallpaper "/path/to/image/image.jpg"
```

---

