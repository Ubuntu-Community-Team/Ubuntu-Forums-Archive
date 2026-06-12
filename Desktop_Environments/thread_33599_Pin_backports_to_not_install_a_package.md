---
title: "Pin backports to *not* install a package?"
date: 2005-05-11
forum: Desktop Environments
---

### Post by darkaudit on 2005-05-11
I have hoary backports in my sources.list, but I'm struggling with setting /etc/apt/preferences. I want to set apt to ignore backport's version of mozilla-firefox and mozilla-firefox-gnome-support. Everything else in backports should show as normal when updates are available.

---

### Post by 23meg on 2005-05-11
in synaptic, choose the packages you don't want updated, and choose "lock version" in the package menu.

---

### Post by darkaudit on 2005-05-11
And what happens when the next hoary-security update comes in? I'd still like that one to show up as available when I do an update.

---

### Post by 23meg on 2005-05-12
hmm, this got me curious as well. i'll try to figure it out, and i'd be happy to hear from the backports crew about how to accomplish this if possible. check out these two docs in the meantime:

[http://wiki.debian.net/?AptPreferences](http://wiki.debian.net/?AptPreferences)
[http://wiki.debian.net/?AptPinning](http://wiki.debian.net/?AptPinning)

---

