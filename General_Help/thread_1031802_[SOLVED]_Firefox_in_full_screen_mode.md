---
title: "[SOLVED] Firefox in full screen mode"
date: 2009-01-05
forum: General Help
---

### Post by purplenite on 2009-01-05
Every time I open Firefox, it opens in a sort of full screen mode (not the normal full screen normally toggled by F11 - my File, Edit, etc. menus are still there, and aren't in normal full screen mode). The only way to restore the normal view is to hit F11 to toggle to real fullscreen, then F11 again to restore the normal window.

I am running 8.10 64-bit and this is Firefox 3.0.5. I haven't upgraded or modified my Firefox install lately, so I'm not sure what has changed. I had the exact same problem with OpenOffice Calc a couple of years ago, and it eventually fixed itself.

---

### Post by blazemore on 2009-01-05
Close Firefox

```
rm -rfv $("locate" *firefox*localstore.rdf)
```

NOT SUDO

---

### Post by purplenite on 2009-01-05
Thank you! All better.

---

