---
title: "Change nautilus desktop location"
date: 2007-02-28
forum: Desktop Environments
---

### Post by Benn on 2007-02-28
Hi. I would like to know how to change Nautilus default "Desktop" location. By default it's '/home/user/Desktop', but I would like to change it to my home directory: /home/user/. I mean, I need to see my home right in my Desktop.

Thanks

---

### Post by ComplexNumber on 2007-02-28
> **Benn said:**
> Hi. I would like to know how to change Nautilus default "Desktop" location. By default it's '/home/user/Desktop', but I would like to change it to my home directory: /home/user/. I mean, I need to see my home right in my Desktop.

Thanks
fire up gconf-editor, go to Edit in the menu, then Find. then type in "nautilus" (don't tick the tickboxes). then look for apps/nautilus/preferences, and tick the 'desktop_is_home-dir' switch.

---

