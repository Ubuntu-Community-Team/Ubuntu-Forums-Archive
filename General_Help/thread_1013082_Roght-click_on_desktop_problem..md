---
title: "Roght-click on desktop problem."
date: 2008-12-16
forum: General Help
---

### Post by Freddy on 2008-12-16
Greetings all.

I did something somewhere and now I can't right-click to get a menu on my desktop. I'm a bit confused about this and do not know what to do about this.

If there are any kind sole out there that knows how I should remedy this situation, you would make me a very happy camper ;).

/Fredrik

---

### Post by Locke_99GS on 2008-12-16
Did you disable Nautilus as the desktop? Try restarting X, if you haven't done so already.

---

### Post by drs305 on 2008-12-16
If you can't do anything on the desktop, like it has a plate of glass over it, and nothing is visible on it (no icons), the Desktop may be 'turned off'.

Run this command to turn it back 'on':
```
gconftool-2 --type bool --set /apps/nautilus/preferences/show_desktop 'true'
```

---

### Post by Freddy on 2008-12-16
> **drs305 said:**
> If you can't do anything on the desktop, like it has a plate of glass over it, and nothing is visible on it (no icons), the Desktop may be 'turned off'.

Run this command to turn it back 'on':
```
gconftool-2 --type bool --set /apps/nautilus/preferences/show_desktop 'true'
```

Thanks, that and a restart of Nautilus did the trick.

---

