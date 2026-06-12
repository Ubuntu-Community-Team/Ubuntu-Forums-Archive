---
title: "Firefox Menu Bar and Items Color"
date: 2008-04-13
forum: Desktop Effects &amp; Customization
---

### Post by rinishak on 2008-04-13
Recently, the colors of the menu bar text and menu item text have turned light gray, rendering it barely visible with my light-colored theme and it only becomes visible when highlighted (since the text is light and the highlight color is quite dark, it becomes visible). I want to know why this problem has surfaced and how to fix it. It may have occurred while I was switching themes; it has been working fine until recently.

I've tried switching back to my previous themes (even the default Ubuntu Human theme), wallpapers, fonts, etc. Nothing works.

And as far as I know, this problem only occurs with Firefox.

Any ideas, anyone?

---

### Post by LennyX on 2008-05-21
I'm probably about a month too late, but I just came across this problem & managed to fix it.

For me it was caused by following directions on a theme site - specifically for the SlicknesS theme ([http://www.gnome-look.org/content/show.php/SlicknesS?content=71993](http://www.gnome-look.org/content/show.php/SlicknesS?content=71993))

To undo the changes, open a terminal & type:
```
cd $HOME/.mozilla/firefox/*.default
rm -r chrome
```

After I did that, I had to change themes in Firefox and then hit restart Firefox for the changes to be recognized.

---

