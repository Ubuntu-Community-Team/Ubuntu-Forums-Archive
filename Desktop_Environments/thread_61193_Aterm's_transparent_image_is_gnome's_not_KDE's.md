---
title: "Aterm's transparent image is gnome's not KDE's"
date: 2005-08-30
forum: Desktop Environments
---

### Post by GoldBuggie on 2005-08-30
Hi

I compiled aterm and started it. I wanted it to have transparent background so I invoked that. But  it shows the wallpaper that I have under gnome. I have earlier installed gnome but KDE is where I started. But how come aterm sees the wrong wallpaper? The regular konsole in Kubuntu works like a charm with transparent background. But I want aterm since it doesn't leave a small border when i only make the workspace visible.

Any help would be appreciated. I would like to get a decent terminal with transparent workspace and nothing else to work.

---

### Post by dialate on 2005-08-30
You can start aterm with
```
aterm -pixmap yourbg.xpm -bgtype [tile|scale|center|etc]
```

It must be an XPM.

To make it always do this, edit your ~./Xdefaults and add:

```
aterm*pixmap:yourbg.xpm
aterm*bgtype:tile
```



You might like eterm better, it supports a wider variety of customization, png and jpegs, etc.

---

