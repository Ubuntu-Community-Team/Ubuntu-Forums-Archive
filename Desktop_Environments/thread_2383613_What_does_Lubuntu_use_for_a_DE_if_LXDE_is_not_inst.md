---
title: "What does Lubuntu use for a DE if LXDE is not installed as a package?"
date: 2018-01-27
forum: Desktop Environments
---

### Post by dajakerboss on 2018-01-27
My laptop (running LXDE on Ubuntu 18.04) was having issues displaying a theme (Color-UI) correctly like my desktop (Lubuntu 14.04.5). I decided I would check on the LXDE version, and all I could think of was trying to install it so it would tell me it was the latest version and I could see the version number.

LXDE was not installed, and I had to panic-abort the installation

If LXDE isn't installed, where is the DE?

---

### Post by cruzer001 on 2018-01-27
Yes they are different DEs, but also the same :)  OpenBox is still the WM on both.

[https://packages.ubuntu.com/bionic/lubuntu-core](https://packages.ubuntu.com/bionic/lubuntu-core)

---

### Post by vasa1 on 2018-01-27
@dajakerboss, is it correct that you're using Ubuntu 1_8_.04?

You wrote> My laptop (running LXDE on Ubuntu 18.04) How did you get LXDE on the system? What was the command? What exactly did you "panic-abort"?

---

### Post by ajgreeny on 2018-01-27
If you really have 18.04 but chose Lubuntu-next, not the usual Lubuntu iso image, you may find you now have LXQt instead of LXDE, as that is the DE Lubuntu is moving towards, though not yet suitable for general use, if my experience is anything to go by.

---

### Post by again? on 2018-01-28
Lxde is a **metapackage**.
Lubuntu-desktop is another **metapackage**.
They may install the same window manager, panel etc and so may be visually similar.
[What is a metapackage?]("https://help.ubuntu.com/community/MetaPackages")

---

