---
title: "[SOLVED] removing desktop environment"
date: 2008-03-22
forum: Desktop Environments
---

### Post by null-cipher on 2008-03-22
I'm not sure how obscure this question is...
but...
I have an Ubuntu installer CD, and I'm looking to put a server together.
Naturally, I don't want a GUI on there, so is there any easy way to remove the GUI and related bits?

sudo apt-get remove ubuntu-desktop

Would that do the trick?

---

### Post by lloyd_b on 2008-03-23
> **null-cipher said:**
> I'm not sure how obscure this question is...
but...
I have an Ubuntu installer CD, and I'm looking to put a server together.
Naturally, I don't want a GUI on there, so is there any easy way to remove the GUI and related bits?

sudo apt-get remove ubuntu-desktop

Would that do the trick?

No - that'll just remove the "ubuntu-desktop" meta-package, but leave behind all of the packages that actually make up the desktop.

If you can download the "Alternate Install" CD, it has an option to install a "command-line only" system with no GUI stuff whatsoever.

If that's not an option, after installing (from one of the virtual consoles):
```
sudo apt-get remove x11-common
```
Because pretty much everything in X depends on this package, this will remove a lot of stuff (a test on my system says 583 packages to be removed).  But I don't guarantee this'll get rid of *everything*.

Lloyd B.

---

### Post by null-cipher on 2008-03-23
Hey thanks!
I'll test that out later.

Much appreciated.

---

