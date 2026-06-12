---
title: "xfce - follow up"
date: 2011-07-14
forum: Desktop Environments
---

### Post by Diametric on 2011-07-14
Hello,

Just a quick follow up thread.  I asked about a week ago about how to install xfce, and so far, I like it.  I can tell that it is noticeably faster than gnome.  I wish it were a bit more polished, but that is a trivial, cosmetic issue.

However, i do have one complaint and that is, it doesn't seem to me that the file browser in xfce allows for multiple tabs ie tabbed browsing.  I often have several different directories I am working in, and having to open multiple windows becomes tedious.  

Other then that I am considering changing my desktop to xfce permentatly.  Anyone know of a fix for this issue>

Cheers!

---

### Post by hhh on 2011-07-14
Thunar doesn't have tabbed browsing, and from what I've read the developer(s) of Thunar don't like or don't use tabs and will never implement that feature. You can quickly open Thunar in a new window by using Ctrl+n (think n for new window).

An alternative is to install another file manager that has tabbed browsing, like PCManFM or Nautilus (both available in Synaptic). If you decide to use PCMAnFM, make sure to turn off Volume Management in either Thunar (Edit>>Preferences>>Advanced) or in PCManFM (can't remember exactly but it's something very similar). If you decide on Nautilus you have to do the same, plus you have to prevent Nautilus from drawing the desktop. You can easily do that by running these 2 commands in a terminal after you install Nautilus but BEFORE you run Nautilus for the first time...

```
gconftool-2 -s -t bool /apps/nautilus/preferences/show_desktop false &
```
```
gconftool-2 -s -t bool /desktop/gnome/background/draw_background false &
```

If for some reason you want to undo those key changes, run them again but replace the word false with true. Hope that helps.

BTW, what looks ugly to you in Xfce? There are a lot of little tricks for making Xfce as pretty as Gnome. PM me if you want, I'd be glad to help.

---

### Post by XubuRoxMySox on 2011-07-14
+1 for the PCManFM file manager! It's powerful, versatile, lightweight, and simple enough even for me!

It's always one of the first things I add to a fresh installation of Xubuntu!

-Robin

---

### Post by Diametric on 2011-07-15
Awesome, I'll give that a whirl and post my results.  thanks!

---

