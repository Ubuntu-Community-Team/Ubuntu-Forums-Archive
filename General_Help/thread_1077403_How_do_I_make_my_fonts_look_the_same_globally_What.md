---
title: "How do I make my fonts look the same globally? What do I do to my .fonts.conf?"
date: 2009-02-22
forum: General Help
---

### Post by wersdaluv on 2009-02-22
Here are my GNOME font settings
[[img]http://www.ubuntu-pics.de/thumb/10051/screenshot_02_C8cEVS.png[/img]](http://www.ubuntu-pics.de/bild/10051/screenshot_02_C8cEVS.png)

[[img]http://www.ubuntu-pics.de/thumb/10052/screenshot_04_6O3yIm.png[/img]](http://www.ubuntu-pics.de/bild/10052/screenshot_04_6O3yIm.png)

I want other apps to have the same font settings including the rendering. Qt apps, OpenOffice.org, and Firefox don't have the same fonts as my GNOME apps. It's probably because I deleted my .fonts.conf. What should my .fonts.conf look like so that I can achieve this?

---

### Post by spiderbatdad on 2009-02-22
```
run command: sudo fc-cache -fv ~/.fonts # to enable fonts in the ~/.fonts file.

```

---

### Post by wersdaluv on 2009-02-22
> **spiderbatdad said:**
> ```
run command: sudo fc-cache -fv ~/.fonts # to enable fonts in the ~/.fonts file.

```
Ran it and the output says that it was successful. What does it do? :D

---

### Post by wersdaluv on 2009-02-22
> **wersdaluv said:**
> Ran it and the output says that it was successful. What does it do? :D
Okay. Now, I have my old .fonts.conf. Thanks! :D

---

### Post by wersdaluv on 2009-02-22
I'm KDE4 right now and noticed that GNOME fonts here don't look as intended now. KDE4 apps have the right fonts on GNOME but GNOME apps don't have the right font rendering on KDE4. Any idea? :)

---

### Post by spiderbatdad on 2009-02-23
hmmm. no other ideas at the moment. Try a google search of kde4 fonts. I think you'll find a few bug reports that might help...or maybe some other ideas. Good Luck.

---

