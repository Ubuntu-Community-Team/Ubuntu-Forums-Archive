---
title: "kde-devel broken"
date: 2005-03-23
forum: Desktop Environments
---

### Post by dawynn on 2005-03-23
(Yes, this was previously posted in the generic hoary forum.  No response there.  Reposting)

OK - I know that this is a Universe package, but it still needs fixing.

kbugbuster is uninstallable because of a missing library. This impacts the installability of kdesdk, kde-devel, and kde-devel-extras.

For some reason, kbugbuster depends on library "libkcal2" which doesn't exist. The Debian unstable version depends on library "libkcal2a" which *does* exist both in Debian, and in Ubuntu.

Is there a reason that the library was changed on this package to make it uninstallable? Can we either get a libkcal2 package built or change kbugbuster so it depends on libkcal2a?

Thanks!

---

### Post by apokryphos on 2005-03-23
It's a known issue; a bug report has been filed for it. Hopefully we'll see some progress on this soon.

---

