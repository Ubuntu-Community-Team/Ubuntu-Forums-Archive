---
title: "Firefox scrunches text"
date: 2009-05-03
forum: General Help
---

### Post by BLTicklemonster on 2009-05-03
How can I get firefox to stop doing this?

[IMG]http://img118.imageshack.us/img118/1118/annoyingffox.jpg[/IMG]


See in the yellow circle? I see that on quite a few sites, and it's annoying. Only happens in Ubuntu, not windows. Is there something I can do?

---

### Post by sgosnell on 2009-05-04
Change the text size, using Ctrl-+/Ctrl--.

---

### Post by kerry_s on 2009-05-04
set the minimum font size to none.

---

### Post by BLTicklemonster on 2009-05-04
> **kerry_s said:**
> set the minimum font size to none.

Thank you. That's been driving me nuts for a while now!

---

### Post by BLTicklemonster on 2009-05-21
Bah, it's still scrunching.

---

### Post by asmoore82 on 2009-05-21
New feature in Version 3 ...

"View -> Zoom -> Zoom Text Only"

This is **_off_** by default but I have to keep it **_on_** - effectively reverting to Firefox2 behaviour.
Firefox3 will remember the zoom level for each individual site
but "Zoom Text Only" applies globally to all sites.

---

### Post by BLTicklemonster on 2009-05-22
Doesn't make any difference for me. :(

---

### Post by asmoore82 on 2009-05-22
Hmmm, interesting, could you post a link to a site known to do it regularly?

---

### Post by BLTicklemonster on 2009-05-22
foxnews.com and [www.intellicast.com](www.intellicast.com) for starters.

---

### Post by bobince on 2009-05-22
The problem in Fox's case is:

> #story .gallery_container p.caption { top: 27em; }

When ‘minimum font size’ is set to None this is fine, it lines up with the ‘height’ of the containing grey box (which is also specified in ‘em’, but it's a bigger ‘em’ because the font-size of the caption is smaller than that of the containing box).

However when ‘minimum font size’ is larger than the stated caption text size, this causes the font-size of p.caption to be artificially increased. This in turn changes the size of ‘27em’ as used in the ‘top’ property. So the top-position gets bigger (moves downwards). But the grey containing box does not get bigger to match because its own font-size has not been affected, and consequently the text falls out of the box onto the article text, rendering it unreadable. It's not a bug; Firefox is doing what it's told, and other browsers with text-size hacks will exhibit the same behaviour.

It's unusual to lay out your whole page (including images!) in ‘em’ units. In principle it should generally work, but it will always risk breakage by crude text-size hacks like text zooming and ‘minimum font size’. Best to avoid these features and stick to page zooming (View->Zoom in Firefox 3 with ‘Zoom text only’ turned off) when the text is too small, if you want to preserve page layouts as the authors intended.

---

### Post by BLTicklemonster on 2009-05-22
So it's just something we have to deal with until page authors catch on? Like that's going to happen... there are still tons of sites that only work well in IE...

---

