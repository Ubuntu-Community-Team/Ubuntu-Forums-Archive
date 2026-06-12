---
title: "Firefox wrecked in power loss"
date: 2009-03-19
forum: General Help
---

### Post by auntie_lovie on 2009-03-19
Lost power and now Firefox doesn't completely load. I type in a URL, and can navigate links, but all Bookmarks and History are gone, and can't make new bookmarks, or even go Back. Have been using Ubuntu for about six months, on a resurrected freebie laptop (Pentium II, Dell CPi)-- kind of a retro-90s netbook. Thanks to all!

---

### Post by fieroboom on 2009-03-19
> **auntie_lovie said:**
> Lost power and now Firefox doesn't completely load. I type in a URL, and can navigate links, but all Bookmarks and History are gone, and can't make new bookmarks, or even go Back. Have been using Ubuntu for about six months, on a resurrected freebie laptop (Pentium II, Dell CPi)-- kind of a retro-90s netbook. Thanks to all!

Sounds like a corrupted conf file somewhere. The simplest thing to do might be to try a reinstall:
```
sudo apt-get install --reinstall firefox-3.0
```
And if that doesn't get things going again, then you'll need to purge it and then reinstall:
```
sudo dpkg --purge firefox-3.0

sudo apt-get install firefox-3.0
```
This is of course assuming you have 3.0. If not, just substitute 'firefox' in place of 'firefox-3.0'
:D
-Paul

---

### Post by auntie_lovie on 2009-03-19
Thanks for the speedy reply!

Tried the reinstall, no go. But then, when I tried Plan B:

~$ sudo dpkg --purge firefox-3.0
dpkg: dependency problems prevent removal of firefox-3.0:
 firefox depends on firefox-3.0.
 firefox-3.0-gnome-support depends on firefox-3.0 (= 3.0.7+nobinonly-0ubuntu0.8.04.1).
dpkg: error processing firefox-3.0 (--purge):
 dependency problems - not removing
Errors were encountered while processing:
 firefox-3.0

(and we know that it is Firefox 3.0.7)
Now I am so confused :(
Thanks again.

---

