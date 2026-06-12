---
title: "A few neverwinter nights issues"
date: 2008-05-30
forum: Gaming &amp; Leisure
---

### Post by kponds on 2008-05-30
Hey all.

I just got neverwinter nights, pretty much on a stock install of Hardy running on a Macbook.

I'm using NWN Diamond, fully patched, no add on modules yet.

Every once in a while, the window goes off of fullscreen and into windowed mode, seemingly at random.  Then it will go back to fullscreen mode.

But, when it goes back to fullscreen mode, there is a second cursor (looks like basic X11 cursor) stuck in the dead middle of the screen.  It stays there the whole time that I am playing.

Anyone know what to do to get around this? Either to stop it from going into windowed mode or to remove the cursor.


Ideally, I would actually like to play in windowed mode.  But when I am in windowed mode, every time I click to move or click on a menu, the dark areas of the screen flash, like the lighting is screwing up.  The macbook doesn't have hardware T&L unfortunately, but is there a way around this?

---

### Post by Perfect Storm on 2008-05-30
Disable compiz while playing nwn will do the trick.
```
metacity --replace
```

---

### Post by Josey on 2008-05-30
Check your nwn.ini under video options.  Change as you wish.

```
AllowWindowedMode=0
FullScreen=1
```

---

