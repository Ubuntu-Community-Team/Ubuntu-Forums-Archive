---
title: "Xine playing media too fast"
date: 2006-02-20
forum: Desktop Environments
---

### Post by pablovp on 2006-02-20
Applications that use xine engine (amaroK,Mplayer,Totem,...etc)plays media too fast.

Im using ATi driver, here is the output from fglrxinfo:

OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON X700 Generic
OpenGL version string: 2.0.5582 (8.21.7)

Any suggestion?

---

### Post by pablovp on 2006-02-20
Solved it...

It was not xine that caused the problem, it's a amd64 clock problem in breeze 32bits.

This was the cause of another problem, my clock was running  too fast, updating it with ntp servers worked,  but in a few minutes it was wrong again.

this thread showed me how to solve it:

[http://www.ubuntuforums.org/showthread.php?t=75281](http://www.ubuntuforums.org/showthread.php?t=75281)

only adding the line:

*noapic *

to the file */boot/grub/menu.lst* after

## ## Start Default Options ##

solved the problem.

---

