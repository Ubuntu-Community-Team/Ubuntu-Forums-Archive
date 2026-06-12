---
title: "GTK Theme Issue"
date: 2008-01-21
forum: Desktop Effects &amp; Customization
---

### Post by alamarco on 2008-01-21
I have an issue with changing my GTK Theme. When ever I change the theme the "text area" stays the same color and thus I can't use custom themes. This happens with the High Contrast themes that come with Ubuntu as well so it's not just the theme I downloaded.

I have Compiz, XGL and Emerald installed and I think it happened around the time when I got compiz, XGL, and emerald working since I remember it working when I first had the system installed.

I'm not even really sure what to search for so I'm kind of stuck in helping myself :(.

Any input is appreciated, thank-you.

Solved: After fooling around I figured it out.

1. Make sure to remove the GTK QT Engine is removed

```
sudo apt-get remove gtk-qt-engine from console
```

2. Make a custom theme with the Appearance preferences

```
System -> Preferences -> Appearance -> Customize -> Choose Dark Theme

3. Use GTK Theme

[code]gtk-chtheme from console
```

---

