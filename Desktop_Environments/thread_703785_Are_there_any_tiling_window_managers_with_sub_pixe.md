---
title: "Are there any tiling window managers with sub pixel font rendering?"
date: 2008-02-21
forum: Desktop Environments
---

### Post by kentl on 2008-02-21
Hi,

Before I dig my way through Ratpoision, wmii, awesome, ion etc I wanted to ask here. Which tiling window managers are there which support sub pixel font rendering? I work with text a lot, preferably in a nice editor like Vim or Emacs. And would like to use sub pixel font rendering as I find it easier on the eyes.

---

### Post by afoglia on 2008-02-22
> **kentl said:**
> Before I dig my way through Ratpoision, wmii, awesome, ion etc I wanted to ask here. Which tiling window managers are there which support sub pixel font rendering? I work with text a lot, preferably in a nice editor like Vim or Emacs. And would like to use sub pixel font rendering as I find it easier on the eyes.

I'm nearly certain sub-pixel rendering is a feature of the programs run, not the window manager itself.  The only exceptions are things like titlebars and the typical desktop stuff like system tray, start menu, task list.

Vim in particular knows nothing about fonts.  It just uses the font of your terminal program.  So if you use (XFCE's) Terminal or gnome-terminal or konsole you can definitely use sub-pixel rendering.  (Gvim is obviously different, but I think all use gtk, so you should have no problems.)

As for emacs, things are a bit more complicated.  I think you need to use a version of emacs patched to use the xft backend.  See [this blog post]("http://peadrop.com/blog/2007/01/06/pretty-emacs/") (the author has packages for hardy in addition to the ones mentioned) and [this Emacswiki page]("http://www.emacswiki.org/cgi-bin/wiki/XftGnuEmacs").

You might have a harder time configuring the subpixel rendering, but either try configuring it from Gnome, KDE, or XFCE and hope it sticks, or do it manually.  [Here's a very old page]("http://jmason.org/howto/subpixel.html") on how to do it.  Googling for [subpixel and xorg]("http://www.google.com/search?q=subpixel%20xorg") returned some more recent documentation for other distributions that should get you started.

---

### Post by kerry_s on 2008-02-22
try here-> [http://xwinman.org/](http://xwinman.org/)

i use jwm, fonts look nice to me.
isn't fonts selectable in the editor?

---

