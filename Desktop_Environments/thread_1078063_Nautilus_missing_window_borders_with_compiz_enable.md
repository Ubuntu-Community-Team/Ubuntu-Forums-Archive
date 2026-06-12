---
title: "Nautilus missing window borders with compiz enabled"
date: 2009-02-22
forum: Desktop Environments
---

### Post by willgorman on 2009-02-22
I'm using Ubuntu 8.04 and whenever I have compiz desktop effects enabled, nautilus loses its window borders (title, minimize/maximize buttons).  It seems to be just nautilus that's affected, other applications still have window borders and if I turn off compiz (set the visual effects to none under system->preferences->appearance) then the window borders reappear for nautilus.  Does anyone know what might be causing this and what I could try to fix it?

---

### Post by blazemore on 2009-02-23
Install the application fusion-icon
```
sudo apt-get install fusion-icon
```

Set it to run at startup in Preferences->Sessions

There'll be an icon in your notification area that has an option to select the type of window border, choose GTK (metacity) or Emerald.

---

### Post by willgorman on 2009-02-23
That's good to know, I already had fusion-icon installed but I didn't know that it could more easily switch between window managers with it.  It's still a little annoying to have to switch back to metacity every time I want to use nautilus though.  Is there anything else to try to get the window decorations to be enabled with compiz?  I currently only have GTK Window Decorator available under the window decorator options.  Are there other window decorators that might work better?

Thanks,
Will

---

### Post by blazemore on 2009-02-24
Emerald or Kwin

---

