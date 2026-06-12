---
title: "Default window position for Firefox"
date: 2011-03-16
forum: Desktop Environments
---

### Post by Jeff Root on 2011-03-16
For the last year I was using the version of Firefox that came
with 32-bit Karmic Koala.  Recently I installed 64-bit Maverick
Meerkat, so I'm now using Firefox 3.6.10.
 
Previously, when first opening Firefox, the window aligned to
the left edge of the screen.  Now it is centered.  The window
dimensions are correctly retained between sessions, but not
the position.  Can I get it to open at the left again?
 
   -- Jeff, in Minneapolis

---

### Post by Krytarik on 2011-03-16
I assume/hope that you are using Compiz (desktop effects)?!

If so, you can specify Firefox' window position at launch with Compiz' "Place Windows" plugins:
"System -> Preferences -> CompizConfig Settings Manager -> Window Management -> Place Windows"

Try to adjust the "Placement Mode" ("General" tab) first, it seems like you have "Center" selected there, the default is "Smart".

If that doesn't work, you can specify a specific rule for Firefox in the "Fixed Window Placement" tab, with a window match like that:
```
(class=Firefox & type=Normal)
```
[http://wiki.compiz.org/WindowMatching](http://wiki.compiz.org/WindowMatching)

If you are not using Compiz, but Metacity, you have to use "Devilspie" to achieve that, its in the official repos.
[http://burtonini.com/blog/computers/devilspie/](http://burtonini.com/blog/computers/devilspie/)
[https://help.ubuntu.com/community/Devilspie](https://help.ubuntu.com/community/Devilspie)

Greetings.

---

### Post by Jeff Root on 2011-03-17
Well.
 
After two days of insisting on opening at the center, this
morning it opened at the left edge.  It must have wanted me
to post here before it would do what I asked.
 
Thanks for your reply, Krytarik.  I may use that, too.
 
   -- Jeff, in Minneapolis

---

