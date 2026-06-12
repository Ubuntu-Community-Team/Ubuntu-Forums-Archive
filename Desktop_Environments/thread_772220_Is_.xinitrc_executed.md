---
title: "Is .xinitrc executed?"
date: 2008-04-28
forum: Desktop Environments
---

### Post by blippy on 2008-04-28
Does ~/.xinitrc get executed when you log in from kdm?

I made some alterations to it to make some tweaks to my keyboard, and nothing seems to have changed.

Also, if .xinitrc isn't called, then is there something else I can use that is equivalent?

---

### Post by bingoUV on 2008-04-28
Try ~/.xsession. It will be run whenever you log in from any display manager.
~/.xinintrc will be executed if you run startx from command line.

---

