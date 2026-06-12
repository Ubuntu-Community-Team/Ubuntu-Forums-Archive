---
title: "Evolution in english"
date: 2007-01-17
forum: Desktop Environments
---

### Post by tassoman on 2007-01-17
Hello to all,
 since yesterday, my evolution is displaying english captions instead localized in italian.

It happened also to the menu item in the gnome panel.

W00t? some help? There isn't any package evolution language to reconfigure, should I take care of gnome localization?

---

### Post by tassoman on 2007-01-17
Bump ](*,) , someone could help? Seems it happened just after locale upgrade

---

### Post by dcstar on 2007-01-17
> **tassoman said:**
> Hello to all,
 since yesterday, my evolution is displaying english captions instead localized in italian.

It happened also to the menu item in the gnome panel.

W00t? some help? There isn't any package evolution language to reconfigure, should I take care of gnome localization?

AFAIK Evolution gets it settings from the system locale, so you probably need to reset/fix them if the update did something.

---

### Post by todoporron on 2007-01-19
Same was happening to me but with spanish.

All you have to do is to reinstall the language-gnome-it packages (or whatever language package) via synaptic and restart gnome.

Good luck

---

### Post by tassoman on 2007-01-19
Yes it was the problem. To solve I've did:

```

sudo apt-get remove language-pack-gnome-it language-pack-gnome-it-base

```

then

```

sudo apt-get install language-pack-gnome-it language-pack-gnome-it-base

```

Last, reboot GUI :mrgreen:

---

