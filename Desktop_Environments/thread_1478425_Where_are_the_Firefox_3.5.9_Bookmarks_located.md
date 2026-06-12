---
title: "Where are the Firefox 3.5.9 Bookmarks located?"
date: 2010-05-09
forum: Desktop Environments
---

### Post by keithld on 2010-05-09
Also what is the name of the file...

Thanks Guys...

---

### Post by DaymItzJack on 2010-05-09
I think I found them in ~/.mozilla/firefox/<letters>.default/bookmarks.html

---

### Post by _0R10N on 2010-05-09
> **DaymItzJack said:**
> I think I found them in ~/.mozilla/firefox/<letters>.default/bookmarks.html

That's right! There is where your bookmarks (for the profile "default") are located. There's also in the same directory, a folder named bookmarkbackups, containing .json files as backups.

---

### Post by lovinglinux on 2010-05-10
> **DaymItzJack said:**
> I think I found them in ~/.mozilla/firefox/<letters>.default/bookmarks.html

Nope. That's an old file from Firefox 2.0 kept for compatibility issues.

In Firefox 3+ bookmarks are stored in a database file, called **places.sqlite**.

---

