---
title: "Restore/replace the standard bookmarks icons?"
date: 2009-12-26
forum: Desktop Environments
---

### Post by Hund on 2009-12-26
How do I restore the bookmarks icons to the defualt settings? And how do I replace them with new icons? I just have blank folder icons now.

---

### Post by Barriehie on 2009-12-26
> **Hund said:**
> How do I restore the bookmarks icons to the defualt settings? And how do I replace them with new icons? I just have blank folder icons now.

The bookmarks file is, at least on my 8.04 install, ~/.gtk-bookmarks  Only way I can think of to restore the initial ones would be to create a new user and then copy that file over.  My 'guest' account .gtk-bookmarks file looks like this:
```

file:///home/guest/Documents
file:///home/guest/Music
file:///home/guest/Pictures
file:///home/guest/Videos

```

Of course change where it says *guest* to your username.
Also, lots of icons in /usr/share/icons/gnome/

HTH,
Barrie

---

### Post by Hund on 2009-12-26
I mean the just the icons. :) My icons are the ones to the right, I want the icons to the left.

---

### Post by Barriehie on 2009-12-26
> **Hund said:**
> I mean the just the icons. :) My icons are the ones to the right, I want the icons to the left.

Been digging on google and it looks like you're going to have to muck around with mime type definitons.  Found a link [here](http://markmail.org/message/o6w7yzswzki7j5pv).

HTH,
Barrie

---

### Post by Hund on 2009-12-26
Hm, there must be a more simple solution. :)

---

### Post by Barriehie on 2009-12-26
Google is yielding /usr/share/icons/-theme name- and /usr/share/pixmaps

Barrie

---

### Post by Hund on 2009-12-31
I solved it with Ubuntu Tweak. Just changed the path for the defualt folders. :)

---

