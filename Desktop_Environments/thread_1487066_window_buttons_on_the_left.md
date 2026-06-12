---
title: "window buttons on the left"
date: 2010-05-18
forum: Desktop Environments
---

### Post by sgerdan on 2010-05-18
I can put them on the right using gconf-editor. But every time I change theme, it goes back to the left. It's annoying. Is there a way to fix them permanently to the right?

---

### Post by sgerdan on 2010-05-18
Hey, I just figured out a way. Change it to the right, then save a new theme in appearance settings. Sorry for the dumb question :)

---

### Post by lisati on 2010-05-18
> **sgerdan said:**
> Hey, I just figured out a way. Change it to the right, then save a new theme in appearance settings. **Sorry for the dumb question **:)

No, it wasn't a silly question. It's good to hear that you found a solution - thank you for sharing it.

---

### Post by sgerdan on 2010-05-18
Thanks. Actually, what I proposed above as a solution may not be working. A better solution is to go to gconf-editor and change the value of button_layout to the desired setting and make it permanent by clicking "Set as Mandatory" in the right click menu.

---

### Post by u-slayer on 2010-05-18
You can fix it with 1 line in the terminal:

```
gconftool-2 --set /apps/metacity/general/button_layout --type string “menu:minimize,maximize,close”
```

---

### Post by arma0012 on 2010-05-20
I followed the terminal advice, which worked, however now my close button has disappeared. Little help?

Cheers,
Sam

---

### Post by arma0012 on 2010-06-10
If anyone is trying this, be sure to add a comma following 'close' in the terminal script provided by g-slayer. This solves the lost close button problem I encountered.

Cheers,
Sam

---

