---
title: "ubuntu 10.04 problem with wobbly windows"
date: 2011-02-26
forum: Desktop Environments
---

### Post by agulanka on 2011-02-26
Hi, I've recently installed Ubuntu and tried to activate the wobbly windows. I have installed drivers for my graphic card and compiz fuzion icon. I've checked the wobbly windows but it doesnt work and I have no idea why... They wobble only when I switch between full screen. They dont wobble at all when I grub them... Any ideas?
Thank you very much :)

---

### Post by agulanka on 2011-03-01
OK, I realized that I have problem with graphic card GF 310M on my Vostro 3500. I've followed many threads about  this issue but none solution worked.... Could you help, please??

---

### Post by Krytarik on 2011-03-01
Although I really don't those plugin ;-), do you have "CompizConfig Settings Manager" installed?

If not, the package is called "compizconfig-settings-manager" and is in the official repos.

Then go to "System -> Preferences -> CompizConfig Settings Manager -> Wobbly Windows" and check the entry for "Move Windows", this is the default setting:
```
Toolbar | Menu | Utility | Dialog | Normal | Unknown
```

---

### Post by agulanka on 2011-03-16
Yeay! You've saved my day! :) Thank you!
Wobbly windows work great.

---

