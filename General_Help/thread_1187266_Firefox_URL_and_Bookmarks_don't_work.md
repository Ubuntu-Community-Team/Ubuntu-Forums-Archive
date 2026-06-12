---
title: "Firefox URL and Bookmarks don't work"
date: 2009-06-14
forum: General Help
---

### Post by setsanto on 2009-06-14
Hi,

I'm having a rather strange problem with Firefox.  My bookmarks menu does not display anything at all, and the URL bar never changes.  For example, I typed "ubuntu forum" into the URL bar in order to get to this forum.  The URL did not change.  In addition, when I clicked on the "General Help" link, the URL still read "ubuntu forum".  Concerning my bookmarks, I've tried restoring my bookmarks, but I keep getting an error message which reads "Unable to process file".  These problems have only started very recently, and I have not updated Firefox recently.

Any ideas?

~Setsanto

---

### Post by lovinglinux on 2009-06-14
Delete the file *places.sqlite* from your Firefox profile, which will be at  ~/.mozilla/firefox/profilename/places.sqlite

---

### Post by setsanto on 2009-06-14
Thanks, that worked perfectly!

~Setsanto

---

