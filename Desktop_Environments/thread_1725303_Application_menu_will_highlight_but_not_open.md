---
title: "Application menu will highlight but not open?"
date: 2011-04-09
forum: Desktop Environments
---

### Post by Dáire Fagan on 2011-04-09
I noticed a few minutes ago that although I can open the Places and System menus fine, when I click on Applications it highlights but no drop down menu appears beneath it as usual, and when I right click and select Edit Menus also nothing happens.

I have since restarted which did not resolve the issue.

How can I remedy this, and have you any idea what could have caused the problem to begin with?

```
mv ~/.config/menus/applications.menu ~/backup.applications.menu
```

The above command resolved it, although I lost some custom launchers to scripts in /opt which I had to recreate.

---

