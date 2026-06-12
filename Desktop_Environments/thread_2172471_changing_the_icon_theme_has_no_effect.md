---
title: "changing the icon theme has no effect"
date: 2013-09-05
forum: Desktop Environments
---

### Post by christoph-pk on 2013-09-05
I'm using gnome-shell 3.6.3.1-0ubuntu6 in Ubuntu 13.04, and gnome-tweak-tool 3.6.1-1.

When opening gnome-tweak-tool, I am able to select one of several icon themes to display; including any themes added to $HOME/.icons/. However, this selection has absolutely no effect on what icons get displayed. Based on the appearance of the file manager icon, the theme that is displayed is Humanity, regardless of which theme is actually selected.

```

$ dconf read /org/gnome/desktop/interface/icon-theme
'oxygen'

$ gsettings get org.gnome.desktop.interface icon-theme
'oxygen'
```

---

