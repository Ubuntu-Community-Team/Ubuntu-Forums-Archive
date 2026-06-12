---
title: "Clear icon text background on Xubuntu?"
date: 2008-02-25
forum: Desktop Effects &amp; Customization
---

### Post by darthchaosofrspw on 2008-02-25
I'm fidgeting around with Xubuntu 7.10 on my laptop. I've been adding stuff so I can make a customized CD (for personal use) with Remastersys 2.0.2. I've also installed a Mac OS X Leopard theme on here along with Mac OS X Leopard icons and some Mac OS X wallpapers.

Anyway, I want to fix my Xubuntu system to where there is nothing surrounding the text on my desktop icons, and I want to change the text color to white. If this is possible, please tell me how it can be done. Thanks in advance.

---

### Post by jmikola on 2008-02-25
this is courtesy of quaaack on the neowin.net forums:

> All you've got to do is add

```
style "xfdesktop-icon-view" {
    XfdesktopIconView::label-alpha = 75

    base[NORMAL] = "#00ff00"
    base[SELECTED] = "#5050ff"
    base[ACTIVE] = "#0000ff"

    fg[NORMAL] = "#ff0000"
    fg[SELECTED] = "#ff0000"
    fg[ACTIVE] = "#ff0000"
}
widget_class "*XfdesktopIconView*" style "xfdesktop-icon-view"
```

to ~/.gtkrc-2.0 . Change the alpha level to 0 to make them transparent. You can also define colours here too.


source: [http://www.neowin.net/forum/lofiversion/index.php/t573919.html](http://www.neowin.net/forum/lofiversion/index.php/t573919.html)

---

### Post by darthchaosofrspw on 2008-02-26
> **jmikola said:**
> this is courtesy of quaaack on the neowin.net forums:




source: [http://www.neowin.net/forum/lofiversion/index.php/t573919.html](http://www.neowin.net/forum/lofiversion/index.php/t573919.html)

Wow. Thanks! Looks even better on here.

---

