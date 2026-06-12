---
title: "How to remove grey background from desktop icons?"
date: 2010-02-10
forum: Desktop Environments
---

### Post by vickoxy on 2010-02-10
Hi,
wanted to ask is it possible to get rid of those grey background on xubuntu desktop icons?

---

### Post by vickoxy on 2010-02-11
Bump!

---

### Post by vickoxy on 2010-02-12
No one tried?

---

### Post by vickoxy on 2010-02-12
Found help here:
[http://ubuntuforums.org/showthread.php?t=228276](http://ubuntuforums.org/showthread.php?t=228276)

i added at the end of my default theme .gtkrc file this text-much better!
But, still what values i need to change to become total transparent background, and that selected icon is not black?

Thanks


```
# this is the new part added by bgryderclock

style "xfdesktop-icon-view" {
    XfdesktopIconView::label-alpha = 75

    base[NORMAL] = "#000000"
    base[SELECTED] = "#000000"
    base[ACTIVE] = "#000000"

    fg[NORMAL] = "#ffffff"
    fg[SELECTED] = "#ffffff"
    fg[ACTIVE] = "#ffffff"
}
widget_class "*XfdesktopIconView*" style "xfdesktop-icon-view"
```

ok-SOLVED:
edit /usr/share/themes/**yourtheme**/gtk-2.0/gtkrc
and add this lines at the end of that file:

> style "xfdesktop-icon-view" {
    XfdesktopIconView::label-alpha = 25

	base[NORMAL] = "#000000"
	base[SELECTED] = "#fdf6f6"
	base[ACTIVE] = "#000000"

    fg[NORMAL] = "#ffffff"
    fg[SELECTED] = "#ffffff"
    fg[ACTIVE] = "#ffffff"
}
widget_class "*XfdesktopIconView*" style "xfdesktop-icon-view"

Then is possible to manipulate the colors there....

Thanks to: bgryderclock

---

