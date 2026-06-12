---
title: "Firefox suddenly lost all bookmarks etc."
date: 2009-01-23
forum: General Help
---

### Post by pwaugh on 2009-01-23
I was browsing, when suddenly I noticed that all my bookmarks were gone and even the home page was changed to the Modzilla default from the Unbuntu default!

I have no idea how this happened, or how to restore them, and worse, it seems that I have no history and cannot now bookmark anything!

Any ideas what I can/should do?

Thanks

---

### Post by pwaugh on 2009-01-23
Ok, managed to solve my own problem.

Turns out it was the installation of Google Earth that caused the problem.

When the installation completes it almost forces you to start it, and most will do so without checking the next step in the install directions which tells you NOT to start it, but to quit as it will run as root if you do (since you ran the install under sudo).

Seems to me this is a big security hole too, but hey.

Anyway, if (like me) you ran it as root by mistake, then all you do to fix it is open a console and type:

~$ sudo chown user:user -R .mozilla

Note, you replace "user" with your user name.  This resets everything to be owned by you, and the group to your group.  Then when you next open FireFox it will all be as it was.

---

