---
title: "How to turn off Desktop Effects when it's broken the desktop?"
date: 2007-08-16
forum: Desktop Effects &amp; Customization
---

### Post by xaindsleena on 2007-08-16
HI All,
I just installed Ubuntu Feisty and I love it, but I unwisely turned on Desktop Effects -> Animations.  It immediately turned my screen white so now I have no idea how to turn it off again to get back to my normal Human desktop theme.

I tried looking in .gnome but it's all in impenetrable XML, and I found some mention on the forums of gconftool-2, but the suggested settings to remove didn't exist.

I'm running on a Dell Inspiron 1501 if that's any help :-)

Best regards
Xain

---

### Post by Seisen on 2007-08-16
As long as you have it set not to save your sessions reboot your computer and it should go back to normal.

---

### Post by xaindsleena on 2007-08-16
Hmm, I only clicked on the "Enable Desktop Effects" button, but it's still enabled when I reboot (even after a power down)

Thanks and best regards
Xain

---

### Post by haricharan on 2007-08-16
i believe its automatically added to the sessions...

go into this directory

```
cd ~/.config/autostart
```

and remove the desktop-effects file if u find it..that way it wont start on startup...

---

