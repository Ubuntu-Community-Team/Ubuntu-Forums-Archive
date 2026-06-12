---
title: "Can't use sawfish in karmic desktop; slow screen refresh outside karmic desktop"
date: 2010-04-13
forum: Desktop Environments
---

### Post by fivebells on 2010-04-13
I have two problems.  They will seem a little strange out of context, but I will describe the problems first, then the context.

**First problem**:  If I go over to a virtual terminal with C-Alt-F2, log in, and start an X session with "startx -- :2", everything starts smoothly, but a few seconds into the session, screen refreshes get very slow: it takes about 1s for firefox to repaint the screen during a scroll, for instance.  Running programs which send a lot of output in an emacs shell becomes pretty tortuous.  I don't see this problem with screen refreshes if I log in in the  usual way.

**Second problem**: If I make sawfish my window manager, and log in using the standard login manager, everything runs fine until I start iswitch-window.  When I do that, the menu listing the available windows shows up, but there is no response to keypresses.  Clicking mouse-1 makes the window menu disappear, but still no response to the keyboard.  Clicking mouse-1 again makes it reappear, and so on in a cycle, but that's the only response I can get.

**Context**: I just upgraded to karmic after a long stretch of using hardy.  In the past,  I've avoided the standard Ubuntu desktop by using the gdm login manager, and starting my own X session in ~/.xsession.  With the latest version of gdm, that no longer works.  I also had problems running gdm-2.20 in its place, although I can't remember exactly what the problem was at the moment.  As an alternative, I started logging in using a virtual terminal and starting my X session with startx as described above.

Basically, I am looking for a solution to one of these problems so that I can get back to work.  

I am pretty addicted to sawfish; I've been using it for the better part of a decade.  iswitch-window is a  particularly useful feature.  However, I am starting to think that sawfish is too old and unused to interoperate cleanly with a modern desktop.

---

### Post by fivebells on 2010-04-13
I [figured out]("https://bugs.launchpad.net/ubuntu/+source/sawfish/+bug/562573") how to fix the sawfish bug, at least.

---

