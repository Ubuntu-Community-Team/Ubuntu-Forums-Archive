---
title: "capslock mapped to control, yet light still comes on"
date: 2008-09-28
forum: Desktop Environments
---

### Post by AvatharTri on 2008-09-28
In Hardy Heron, I have my capslock key mapped to control using the layout options under System->Preferences->keyboard. Before hardy, this would stop the capslock light from lighting up when I press capslock, and this is the desirable behavior. However, under hardy the light still comes up, causing me visual irritation in low-light environments when making heavy use of capslock as control.

How can I disable the light?

---

### Post by olejorgen on 2008-09-29
That's strange.. try running ```
xmodmap -e "clear Lock"
```

---

### Post by AvatharTri on 2008-09-29
that works, thank you. What is the easiest way to add such a script to my session on startup?

---

### Post by olejorgen on 2008-09-29
iirc look in system->preferences->session->startup programs if you use gnome

---

