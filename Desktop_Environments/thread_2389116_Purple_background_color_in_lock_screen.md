---
title: "Purple background color in lock screen?"
date: 2018-04-11
forum: Desktop Environments
---

### Post by kawazu on 2018-04-11
Folks, 

using vanilla GNOME and GDM on Ubuntu 18.04 pre-releases, is there *any* way to make the background color of the GNOME lock screen match the one of the GDM login screen? In the login screen, there's what seems to be a dark-grey background while the default lock-screen background apparently is some sort of purple. I've been browsing around the web a bit and managed to find some resources recommending to play with gdm3.css which I tried - only to figure out I can easily change the login (gray) background color to anything else but apparently the lock screen purple is completely unaffected by those changes. What to do to make these two screens match?

TIA and all the best,
Kristian

---

### Post by SlidingHorn on 2018-04-11
I'm looking at an older source, however, in that same CSS file, look for (or create) the #lockDialogGroup ID and see if that changes it for you

---

### Post by kawazu on 2018-04-11
> **SlidingHorn said:**
> I'm looking at an older source, however, in that same CSS file, look for (or create) the #lockDialogGroup ID and see if that changes it for you

Yes I actually changed that, however it didn't seem to affect the lock screen but rather the login screen background? I *think* I already fixed it this way before, but it doesn't seem to work at least on my current 18.04 install... :|

---

### Post by mlorenzana on 2018-04-20
I had the same issue, but only on Unity. Same change to ubuntu.css worked for me.

---

