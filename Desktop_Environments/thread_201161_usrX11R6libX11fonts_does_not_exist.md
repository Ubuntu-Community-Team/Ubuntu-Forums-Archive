---
title: "/usr/X11R6/lib/X11/fonts does not exist"
date: 2006-06-21
forum: Desktop Environments
---

### Post by reuben on 2006-06-21
I use MainActor for video editing; previously I was running on Breezy, and everything was fine. Now, however, it can't find the fonts on the system (which it needs to be able to render text.) Their support people say that it looks at: /usr/X11R6/lib/X11/fonts, which does not exist on my system.

It appears that I have the major font packages installed; should I create a softlink in place pointing at somewhere else? Is there another alternative?

Thanks

---

### Post by remy215 on 2008-07-16
Hey,
2 years later I have a similar problem.
In fact these fonts were already on my computer but not at this place.

To find them I ran:
- sudo updatedb
- locate fonts | grep 75dpi
=> they were @ /usr/share/fonts/X11/

I've created a symlik to this location:
- 'sudo mkdir /usr/X11R6/lib/X11'
- 'sudo ln -s /usr/share/fonts/X11 /usr/X11R6/lib/X11/fonts'

I hope it helps

:popcorn:

---

