---
title: "Emacs transparent integration"
date: 2009-06-22
forum: General Help
---

### Post by blackxored on 2009-06-22
Hi. 
I don't know if anyone has solved this already, or haven't bothered at all. But I'm needing that Emacs integrate more cleanly into my ubuntu installation. 

These are two issues I've found, (I'll expand later)

- How to set font antialiasing (LCD).
- How to use human GTK toolbar and icons.
- How to make emacs open a file without splitting the welcome window and the file itself.

Hope someone can help.

---

### Post by Brandon Williams on 2009-06-22
For the GTK toolbar and icons, which version of emacs did you install. I see a few different GUI versions of emacs that require libgtk and thus will use your configured GTK icon theme: xemacs21-gnome-*, emacs22-gtk, and emacs-snapshot. The xemacs21-gnome-* packages require libgtk1.2, so the toolbar might not look as you expect with that version, but both emacs22-gtk and emacs-snapshot will definitely fit right in.

For the split window at startup, you simply need to disable the "splash" screen. Start emacs with --no-splash or add '(setq inhibit-splash-screen t)' to your ~/.emacs file.

For font anti-aliasing, [look here](http://ubuntuforums.org/showthread.php?t=1157384).

---

### Post by blackxored on 2009-06-22
Thanks. 
Actually I have emacs22-gtk, I'm installing emacs snapshot right now. Seems to have gtk icons, and I've read the post about antialiasing.

Thanks for all.

---

