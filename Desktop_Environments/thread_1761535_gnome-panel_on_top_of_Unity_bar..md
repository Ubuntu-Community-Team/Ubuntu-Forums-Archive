---
title: "gnome-panel on top of Unity bar."
date: 2011-05-18
forum: Desktop Environments
---

### Post by Netich on 2011-05-18
Ive been trying to have a minimal gnome-panel to place some gnome applets. You can actually have a non extended panel and place it on top of the unity bar, and it looks quite nice.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=192529&stc=1&d=1305723865[/IMG]

The problem is when you use unity the panel, the gnome panel lose focus and stays behind, so a temporary solution is to extend it some pixels to put it on top.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=192530&stc=1&d=1305723865[/IMG]

Is there any way to tell gnome-panel to stay allways on top of unity?

Thanks

---

### Post by Krytarik on 2011-05-18
Try using Compiz' "Window Rules" plugin therefore:
"CompizConfig Setting Manager -> Window Management -> Window Rules"

Enable it and add this to its "Above" field:
```
class=Gnome-panel
```
Greetings.

---

