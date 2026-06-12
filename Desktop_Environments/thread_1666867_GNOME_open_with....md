---
title: "GNOME open with..."
date: 2011-01-14
forum: Desktop Environments
---

### Post by tommy1987 on 2011-01-14
I'm trying to open jpg files with Gwenview by default but instead they try and open with Wine Internet Explorer (don't ask me why).

I've tried right clicking on the file, "open with..." then selecting Gwenview and ticking "Remember this selection for JPEG files". It opens in Gwenview but then when I try to open other images by double clicking on them they open right back in Wine Internet Explorer (which throws an error: DDE Failure).

Any ideas?

---

### Post by tommy1987 on 2011-01-20
shameless attempt to bump...

---

### Post by endotherm on 2011-01-20
search for a thread called "Places menu does not open with nautilus" from a couple years ago. on the last couple of pages folks will be talking about the mimeapps.lst file. this is likely where the bad setting is stored so check out thee thread, open the file, and see if you have any references to wine associated with .jpg mime types.

---

### Post by tommy1987 on 2011-01-20
Thanks for that, solved my problem.

---

### Post by tommy1987 on 2011-01-20
Thanks for that, solved my problem.

---

