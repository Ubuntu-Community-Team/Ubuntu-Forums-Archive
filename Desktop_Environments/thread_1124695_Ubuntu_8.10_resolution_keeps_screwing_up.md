---
title: "Ubuntu 8.10 resolution keeps screwing up"
date: 2009-04-13
forum: Desktop Environments
---

### Post by Necrom@ncer on 2009-04-13
I just did clean install of newest ubuntu on my IBM thinkpad t30, it has a ATI radeon 7500 video card, my GUI got messed up with the screen res, so I restarted, got the same screen so I stopped the gui ctrl+alt+F4. My question is a noob's, how do you edit xorg.conf without gedit, what command?


Nevermind

---

### Post by OldManRiver on 2009-04-13
N,

vi or nano right?

Cheers!

OMR

---

### Post by djbushido on 2009-04-13
if the screen resolution is messed up, first make sure that there is a mode for it in xorg.conf.
Second, if you make it to the login screen, try and reset X with Ctrl-Alt-Backspace, that usually fixes it for me.
Anyway, to edit I use nano, it's not nearly as confusing as vi.
BTW, why would you use a code editor for text editing? Gedit is at least only syntax highlighting...

---

### Post by Necrom@ncer on 2009-04-14
because i'm a noob, and I am trying to learn dos and *NIX commands and because of that often forget the right commands

---

