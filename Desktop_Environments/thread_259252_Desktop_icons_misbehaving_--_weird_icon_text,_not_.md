---
title: "Desktop icons misbehaving -- weird icon text, not lining up."
date: 2006-09-17
forum: Desktop Environments
---

### Post by MikeBenza on 2006-09-17
My desktop icons are a bit weird: their text is somewhat large for a desktop icon, and the text for them wraps after an unreasonably short distance.  Also, they don't automatically align to a grid, even though I have 'Keep Aligned' checked when I right click on the desktop.

Anyone have this problem / know how to fix it?

---

### Post by MikeBenza on 2006-09-17
After a bit of playing around, I've discovered that they icons are *kinda* kept aligned -- they're aligned into vertical columns which overlap (as you can see from the above image), but they're not aligned into rows.  Anyone?


EDIT:
After some more playing around, I got the wrapping issue fixed with gconf-editor: apps -> nautilus -> icon view -> default_use_tighter_layout

I also found apps -> nautilus -> preferences -> desktop_font, which was set to 'Sans 10'.  I changed it to 'Sans 8' and ran killall nautilus to restart it, but there was no effect.  The icons on my desktop did disappear and reappear, so I think they were reloaded.

However, I then found System -> Prefences -> Font.  I changed the desktop font.  Now my only problem is aligning nicely.

- Mike

---

### Post by macarena_unspoiled on 2008-02-12
hi guys !!
I have recently installed ubuntu 7.10.
My problem is that the icon text doesn't wrap at all.Due to this the whole alignment of icons gets distorted and it looks weird.any solution to get the icon text wrapped???

---

