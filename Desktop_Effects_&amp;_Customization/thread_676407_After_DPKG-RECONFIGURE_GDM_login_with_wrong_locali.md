---
title: "After DPKG-RECONFIGURE: GDM login with wrong localization?!"
date: 2008-01-23
forum: Desktop Effects &amp; Customization
---

### Post by perixx on 2008-01-23
Hi everybody!

I was doing and 'dpkg-reconfigure -phigh xserver-xorg' command during the process of changing my ATI drivers with Nvidia's some time ago. Though I was prepared to re-enable my localization and keyboard layout in the settings manager - and did so - I wasn't aware of the fact, that it wouldn't also bring back the right language for GDM's login-page!

Now I've got English keyboard layout for login page at every boot-up... how can I fix this, please?

perixx

---

### Post by perixx on 2008-01-24
Anybody got an idea?

---

### Post by perixx on 2008-01-26
*bump*

---

### Post by FuturePilot on 2008-01-26
It possibly could have detected your keyboard incorrectly.
Run
```
sudo dpkg-reconfigure xserver-xorg
```
This won't auto-detect anything as opposed to the -phigh option.

---

### Post by perixx on 2008-01-27
Hi FuturePilot...

I've ran that command several times since I first encountered the problem, so this doesn't seem to solve the matter..!

perixx

---

