---
title: "Cairodock OpenGL unable to create launchers"
date: 2009-08-17
forum: Desktop Environments
---

### Post by Baggyeyes on 2009-08-17
I installed Cairo Dock from a .deb some time ago and although there would be occasional problems creating launchers for certain programs it was usually underused and obscure programs for which this was the case.

For reasons I can't explain my Firefox launcher was removed and I was unable to create a new one, after some testing I found that I can no longer create launchers at all regardless of what method I try or what program I am creating one for.

I am able to edit launchers to my hearts content, it is only creating them that causes a problem.

Just wondering if anyone could shed any light on this? (apologies for my lack of ubuntu experience)

-Baggyeyes

---

### Post by fabounet on 2009-08-18
what gives ```
ls -l ~/.config/cairo-dock/current_theme/launchers
``` ?
try to do 
```
chmod -R 777 ~/.config/cairo-dock
```

---

