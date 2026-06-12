---
title: "Flash plugin not at correct depth"
date: 2006-06-25
forum: Desktop Environments
---

### Post by evil_elman on 2006-06-25
The FireFox Flash plugin is behaving in a weird way.

Problem #1 -- Flash content is rendered in front of other website content... Normal behaviour should be that it is behind everything else.

The behaviour can be reproduced on these websites, there are probably others:
* [http://www.sephiroth.it/](http://www.sephiroth.it/) (The 'Forums' menu is behind the Flash movie)
* [http://www.ati.com/](http://www.ati.com/) (The menus are painted behind the Flash movie)
* [http://www.adobe.com/](http://www.adobe.com/) (Menu at the top is behind the Flash movie)

Problem #2 -- When using the scroll wheel on a website everything is fine... Until you try to use the scrollwheel while the mouse pointer is hovering on top of a Flash movie. The scrollwheel isn't working while on a Flash movie...

I've tried searching both Ubuntu and Mozilla forums and I don't know where the issue lies (X, FGLRX, Flash Player, Mozilla or somewhere else?).

Screenshot of problem #1 : [http://www.rotoni.net/file_upload/ati_website.png](http://www.rotoni.net/file_upload/ati_website.png), notice that the menu should be in front of the Flash animation beneath.

Any ideas?

**EDIT:** I can now see that it seems to be a bug ([https://bugzilla.mozilla.org/show_bug.cgi?id=207256](https://bugzilla.mozilla.org/show_bug.cgi?id=207256)) which is still open it seems... Any news on this?

Further info: Problem #1 is also reproducible in Opera 9. Seems to be the Flash plugin rather than the browsers that's dodgy.

---

