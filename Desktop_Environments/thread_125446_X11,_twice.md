---
title: "X11, twice"
date: 2006-02-03
forum: Desktop Environments
---

### Post by thechris on 2006-02-03
firstly i will explain the problem, as it is always the first Q asked...
I want to run a remote app, icd.  icd requires X11 to be in 8bit color mode.  gnome/kde use some of the colors leading to great message boxes like:
Question:  (black box)
Answer:  (black box)(black box)(black box)

basically in kde/gnome, i don't know what i am being asked, or what i answered, just that clicking something gets rid of the message...  not useful.

further, the desktops need to be HUGH.  X11 has virtual desktop capabilities, which i've used in the past.
----------------------------------------------------
What i try to do:  run fluxbox on a second X11 session using a custom xorg.conf that sets virtual desktop size and 8bit color.

What happens:  the second X11 servers exits.  no errors are in Xorg.1.log (this is the correct log for :1 ) (that may show up as an emoticon.  it is : 1 without the space).

this worked in gentoo.

also, i cannot run startx as a user.  i need to do this, as attempting startx -- :1 as root sometimes messes up my current xsession.

---

### Post by thechris on 2006-02-04
ok, it seems that X11 starts on VC9 instead of VC8 like in gentoo.  so i can get to my second X11 session.

but once i launch a second X11 session, my first one stops working!  i can't launch new apps at least.

---

