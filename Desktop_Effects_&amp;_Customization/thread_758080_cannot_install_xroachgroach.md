---
title: "cannot install xroach/groach"
date: 2008-04-17
forum: Desktop Effects &amp; Customization
---

### Post by sevensevens on 2008-04-17
This started as an well worn unix joke (installing xroach on yours/someone else's machine and wait), but as yet there have been no roaches crawling around my windows.  I'd like to install xroach (groach now) on my ubuntu box, but it will not work.  When I install from the repository (sudo apt-get install groach), and run groach in the command line, nothing happens (I've tried groach eyes, groach roaches, etc).  It "runs" as in hang the console, but no creepy crawlies appear beneath my window.  I decided to try an install from source, here's some of the output I got from ./configure

```
...
checking for gnorba libraries... (cached) yes
Unknown library `gtkxmhtml'. Install the libgtkxmhtml-dev package
checking extra library "applets"... Unknown library `applets'
...
```

configure finishes, but when I type make, I get

```
...
amain.c:90: error: expected ‘)’ before ‘*’ token
amain.c: In function ‘groach_data_delete’:
amain.c:140: error: ‘GroachData’ has no member named ‘theme_search’
amain.c:150: error: ‘GroachData’ has no member named ‘root_win’
amain.c: In function ‘create_widgets’:
amain.c:156: error: ‘AppletWidget’ undeclared (first use in this function)
amain.c:156: error: (Each undeclared identifier is reported only once
amain.c:156: error: for each function it appears in.)
amain.c:156: error: ‘applet’ undeclared (first use in this function)
amain.c:156: error: ‘GroachData’ has no member named ‘applet’
amain.c:168: warning: implicit declaration of function ‘applet_widget_add’
amain.c:196: warning: implicit declaration of function ‘applet_widget_set_tooltip
...
```

Anyway, I'd like to get xroach running - any advice?

---

