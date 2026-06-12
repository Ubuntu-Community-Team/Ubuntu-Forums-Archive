---
title: "I have both GDM and KDM-KDE4 installed, but cannot start KDE4 normally"
date: 2008-05-25
forum: Desktop Environments
---

### Post by tjksn on 2008-05-25
What I get when I start KDE4 is the desktop, but no taskbar or network manager.  Do I need to change the login manager in order to get the right desktop manager to load?  If so how do I do this?  I cannot find anything that will let me do this.

Tom

---

### Post by Xiong Chiamiov on 2008-05-26
There are still quite a few odd things happening in KDE4.  I haven't actually been able to get my KDE4 desktop to load since when I first installed it.  You can try renaming (effectively deleting but keeping files incase you need 'em) your kde folder, like
```

mv ~/.kde4 ~/.kde4_old

```
then relaunching KDE.  It might solve your problem.

---

