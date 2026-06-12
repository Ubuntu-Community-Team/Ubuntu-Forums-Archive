---
title: "Beryl Problem - Widgets disappear"
date: 2007-05-06
forum: Desktop Effects &amp; Customization
---

### Post by mogwai on 2007-05-06
I find that when I run beryl-manager, sometimes my widgets disappear [[see here]("http://homepages.slingshot.co.nz/~t.hodder/nick/Screenshot.png")].
I have tried adding the following lines to my xorg.conf (under the Screen section):
```
    Option         "AddARGBGLXVisuals" "True"
    Option         "DisableGLXRootClipping" "True"
```
but am still having problems, although a ctrl-alt-backspace seems to temporarily fix it.

Help please!


Ubuntu 7.04
AMD64 3000+
ATI 9200SE

---

