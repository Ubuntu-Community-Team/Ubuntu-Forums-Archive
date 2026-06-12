---
title: "My desktop not at all showing up.."
date: 2010-01-28
forum: Desktop Environments
---

### Post by kumarat9pm on 2010-01-28
when i logged in to ubuntu today its shows me login screen but when i try to login.. it just shows me a terminal in that gui nothing more than that..
how to resolve this issue?

---

### Post by lidex on 2010-01-28
Try running this command:
```
sudo apt-get install --reinstall gdm && sudo dpkg-reconfigure gdm
```

If that doesn't work try this:
```
startx
```
Then run the first command from a terminal when you reach the desktop.

---

### Post by kumarat9pm on 2010-01-28
i removed evolution, which removed my gnome desktop..
reinstalled ubuntu-desktop every thing working fine now.. thanks for the inputs..

Surendra,
[www.linuxnix.com](www.linuxnix.com)

---

