---
title: "How do I turn off window decorations!!!!!"
date: 2007-12-25
forum: Desktop Effects &amp; Customization
---

### Post by always_available on 2007-12-25
I am putting in the mac 4 lin, but my stupid desktop settings manager turns on window decoration and now its red. If I turn off window decoration, the border disapears, so im stuck with it can anyone help!!

---

### Post by Islington on 2007-12-25
did replaceing with metacity work?

---

### Post by shareMenaPeace on 2007-12-25
Did you tried useing failsafe login?

Maybe you ned to uninstall emerald (if this is installed - see in synaptic)

---

### Post by Forlong on 2007-12-26
> **always_available said:**
> I am putting in the mac 4 lin, but my stupid desktop settings manager turns on window decoration and now its red.
That's because you have Emerald installed. You should always keep track on what you install. Do not install anything just because somebody tells you to, if don't know what it does.

Run this via [Alt]+[F2] ```
gtk-window-decorator --replace
```

If you don't want to use Emerald anyway, just remove it:
```
sudo apt-get remove emerald && sudo apt-get autoremove
```

If you want to use GWD but like to have Emerald installed, see here: [http://ubuntuforums.org/showthread.php?p=3746149#post3746149](http://ubuntuforums.org/showthread.php?p=3746149#post3746149)

---

