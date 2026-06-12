---
title: "Applications become unresponsive after autocomplete popup"
date: 2011-11-21
forum: Desktop Environments
---

### Post by johnnyaug on 2011-11-21
Hi all,

I was going to report a bug, but I'm not really sure what package this bug has to do with.

After upgrading to 11.10, when an auto-complete pops up, I cannot type anymore until I alt-tab from the window and back. This happens in textboxes on HTML forms in Google Chrome, and with Content Assist on Eclipse 3.7. I found this bug report for Eclipse:
[https://bugs.eclipse.org/bugs/show_bug.cgi?id=319123](https://bugs.eclipse.org/bugs/show_bug.cgi?id=319123)

which describes a part of my problem, but for me it happens on Chrome as well. I too installed Android plugin for eclipse, but I deleted it, and the problem remains.


Any ideas?

Thanks,
Johnny.

---

### Post by johnnyaug on 2011-11-24
Bumping

---

### Post by LinuxFan999 on 2011-11-24
Does this happen with Firefox too?

---

### Post by johnnyaug on 2011-11-25
Hi,
I just found a fix that works for me:
[https://bugs.launchpad.net/ubuntu/+source/scim/+bug/163325](https://bugs.launchpad.net/ubuntu/+source/scim/+bug/163325)

Apparently it's a matter of SCIM configuration.

---

