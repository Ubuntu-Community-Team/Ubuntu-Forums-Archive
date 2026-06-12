---
title: "gnome and xterm"
date: 2009-06-24
forum: Desktop Environments
---

### Post by frritchi on 2009-06-24
Hi,

I normally launch xterm from within gnome with the command:

"xterm -fg orange -bg black"

After the xterm opens I press cntrl, right click on the terminal and choose "large" for VT fonts.

How can I set xterm to start with the large font?

Thanks,
Frank

---

### Post by kerry_s on 2009-06-24
you can create a alias in ~/.bashrc>
**alias xtrem='xterm -fg orange -bg black -fa "mono-10" '**

or 

create a ~/bin/xterm override>
[B]mkdir ~/bin
nano ~/bin/xterm[/B]

[B]#!/bin/sh
/usr/bin/xterm -fg orange -bg black -fa "mono-10" "$@" &[/B]

**chmod +x ~/bin/xterm**

(note: you must log out & back in)

or

use a .Xresources file

[B]XTerm*faceName: Mono
XTerm*faceSize: 10
XTerm*background: black
XTerm*foreground: orange
[/B]
add to ~/.profile:

[B]if [ -f $HOME/.Xresources ]; then
  xrdb -merge $HOME/.Xresources
fi[/B]

(note: you must log out & back in)
(Xresources might be Xdefaults, i think both work though)

---

### Post by frritchi on 2009-06-24
Hi Kerry,

Unfortunately that seems to change the font. (I did install Microsoft fonts) Is there a way to determine which is the default font xterm uses, or what it is when I change the size to large?

Thanks,
Frank

---

### Post by kerry_s on 2009-06-25
> **frritchi said:**
> Hi Kerry,

Unfortunately that seems to change the font. (I did install Microsoft fonts) Is there a way to determine which is the default font xterm uses, or what it is when I change the size to large?

Thanks,
Frank

sorry, i'm use to using mono. stock fonts are fixed:
bashrc:
**alias xtrem='xterm -fg orange -bg black -fn 9x15 '**

Xresources:
**XTerm*font: 9x15**

---

