---
title: "Jammy Top bar: issue with Places-Status-indicator"
date: 2022-09-15
forum: Desktop Environments
---

### Post by col48 on 2022-09-15
Fresh install of Jammy, now down to the annoying relatively trivial things.

I added Tweaks, Applications indicator, Places Status indicator.

The Places Status Indicator, when selected, shows the default(?) menu - Home, Desktop, Documents... Computer, Browse Network but the only one of these which does anything is the last.
The display for Browse Network is clearly vanilla Nautilus (trying to show Windows Networks, of which there aren't any) and the sidebar entries there work as expected.

**What can I do to get the other Places menu items to do the expected?**
I've found a couple of locations on the file system where there are lists which might be relevant ~/.config/user-dirs.dirs and ~/.config/gtk-3.0/bookmarks but there is clearly more to it than that.

---

### Post by tea for one on 2022-09-15
> **col48 said:**
> What can I do to get the other Places menu items to do the expected?

I'm not sure what the the default expected behaviour is?
I thought it was simply a quick access to favourite places/directories without opening Nautilus.

If you add a new bookmark in Files (nautilus), it then appears in Places Status Indicator.

---

### Post by col48 on 2022-09-15
@tea for one
You've described precisely the behaviour I expect.  But it doesn't happen.  

I would not expect to have to define 'Desktop', 'Documents' (etc) as bookmarks, shouldn't this be defaulted?  But there must be somewhere the indicator looks to find where these folders actually are, just in case the user has moved them (I haven't, by the way)?  Maybe it is a list of bookmarks - if so I don't know where to check to see if these entries are somehow missing or incorrect.

---

