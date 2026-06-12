---
title: "font sizes in .Xresources being overwritten"
date: 2010-10-11
forum: Desktop Environments
---

### Post by noahlt on 2010-10-11
I set some options for font colors, sizes, etc., in my .Xresources file, which is listed at the end of this post.  When I log in to Gnome using GDM, my fonts in rxvt and emacs are too small.

However, if I reload the file using "xrdb .Xresources", any later instances of emacs or rxvt use the fonts I specified, so I know that the .Xresources file is correct.

Furthermore, I know that the file is being read at login because I can observe its effects (for instance, the "plain" scrollstyle for rxvt) even before I reload the .Xresources file.  This makes me suspect that X's settings for font sizes is being overwritten by Gnome during login.

Googling didn't turn up this specific issue.  Anyone have any tips?  Thanks in advance for those who do!

```
! noahlt's .XResources file
URxvt.scrollBar_floating: true
URxvt.scrollstyle: plain
URxvt.scrollBar_right: true
URxvt.font: xft:Inconsolata-8

emacs.background: rgb:00/00/00
emacs.foreground: grey85
emacs.font: Inconsolata-8
emacs.fontBackend: xft
emacs.menuBar: off
emacs.toolBar: -1
emacs.verticalScrollBars: off

```

---

