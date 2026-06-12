---
title: "WINDOW_MANAGER in .gnomerc ignored"
date: 2012-09-24
forum: Desktop Environments
---

### Post by srockets on 2012-09-24
I've been using Ubuntu 12.04.1 with "Gnome Classic" desktop, using [bluetile]("http://bluetile.org/") as my window manager, by having the following line in my ~/.gnomerc:

[FONT="Courier New"]export WINDOW_MANAGER="/usr/bin/bluetile"
[/FONT]
But since last week, that stopped working, and my gnome sessions always use metacity as the WM. I override that by manually running bluetile. 

Unlike my desktop, where I rarely shut it down or log out from it, on my laptop, and hence get shut down from time to time. And manually running bluetile everytime is an annoyance. 

~/.xsession-errors shows no relevant errors.

How can I make my gnome session respect my WINDOW_MANAGER setting?

---

