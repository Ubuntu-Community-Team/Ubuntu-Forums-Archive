---
title: "Gnome panels faster unhide"
date: 2009-02-18
forum: Desktop Environments
---

### Post by Erthainel on 2009-02-18
Hello to all fellow ubuntists :)

I wish to make my panels in GNOME (ubuntu 8.10) unhide faster so i didnt have to wait 1.5 secs every time. This has surely been taken care of somehow. I looked through several HOW-TO's, but none worrk for me. Please help!

---

### Post by Shazaam on 2009-02-18
Open Configuration editor (Applications>System Tools>Configuration Editor). Go to apps>panel>toplevels>panel0 (and top_panel_screen0)> unhide_delay. Set them as you wish.
You can also open it with this in terminal...
```
gconf-editor
```

---

### Post by Erthainel on 2009-02-25
Hi, both set to 0, logout-login and still not immediate. Any other ideas where the problem might be? Thanks anyway.

---

