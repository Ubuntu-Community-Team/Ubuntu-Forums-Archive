---
title: "gksudo has no theme"
date: 2011-10-23
forum: Desktop Environments
---

### Post by suffah on 2011-10-23
I guess since 11.10 is using Unity, the old trick of symbolic linking to the current users gnome themes/icons no longer works.

Is there a fix for this?

I hate launching programs (gns3) with no theme.

Thanks!

---

### Post by gsmanners on 2011-10-23
Aside from copying your theme into /usr/share/themes? I doubt it. Here's how I handled that:

```
sudo cp -r ~/.themes/Clearwaita /usr/share/themes
```

I then switched current theme to something else, deleted the ~/.themes/Clearwaita folder, then switched back to Clearwaita.

---

