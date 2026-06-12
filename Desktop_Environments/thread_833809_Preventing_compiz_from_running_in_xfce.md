---
title: "Preventing compiz from running in xfce"
date: 2008-06-18
forum: Desktop Environments
---

### Post by richardq on 2008-06-18
I'm trying out xfce4 on Hardy. I've been running the standard Gnome with both Compiz and Metacity. I installed the xfce4 metapackage and it all works fine, except that xfce uses Compiz by default. How can I make it use xfwm4 by default?

I can get xfwm4 running manually using 

```
pkill compiz && xfwm4
```

but this doesn't hold when I log out and back in. It always goes back to Compiz. Is there some gnome startup script that xfce is running that launches Compiz? I can't even change any window manager settings using the Settings dialog since it tells me that I'm using an <unknown> window manager (when I'm running xfwm4 manually from a terminal).

Any ideas? 

Thanks. RQ

---

### Post by SkonesMickLoud on 2008-06-19
You could try adding that to your startup script.

Not sure where to go to do that in XFCE though.

---

