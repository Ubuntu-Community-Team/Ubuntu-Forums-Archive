---
title: "How do I change Firefox GUI font?"
date: 2008-07-25
forum: Desktop Environments
---

### Post by loopeando on 2008-07-25
I've set my font to DejaVu Sans Condensed 8 on my desktop but Firefox GUI font didn't change at all.

How can I set my Firefox GUI font to DejaVu Sans Condensed?

Thx!

---

### Post by ibutho on 2008-07-25
What desktop environment are you using? If its GNOME or XFCE, then firefox should follow their settings because its a gtk2 application. If its KDE or anything else, then you need to run a gtk2 configuration tool (e.g. gtk2-chtheme) and change the fonts.

---

### Post by loopeando on 2008-07-25
Solved it by editing userChrome.css, I just had to add this:

```
* {

font-family: "DejaVu Sans Condensed";

}
```

Thx anyway!

---

### Post by listdata on 2008-11-11
> **loopeando said:**
> Solved it by editing userChrome.css, I just had to add this:

```
* {

font-family: "DejaVu Sans Condensed";

}
```

Thx anyway!

Thanks, this did the trick. But I had to disable/enable FF themes (switch back from Whitehart to the Default theme in the Addons -> themes options) to get it to work.

---

### Post by Nen on 2008-11-11
Thanks. I was looking for this info. Btw, it is just me or this method is way more complicated and unintuitive than it should be? Why can't you change the font from Firefox settings like in Windows and OS X?

Edit: Especially considering how damn ugly and unprofessional Ubuntu's default font looks on webpages >.>

---

