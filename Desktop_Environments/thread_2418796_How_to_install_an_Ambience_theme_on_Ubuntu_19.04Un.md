---
title: "How to install an Ambience theme on Ubuntu 19.04/Unity"
date: 2019-05-11
forum: Desktop Environments
---

### Post by van hanegen on 2019-05-11
Hi,
just installed Ubuntu 19.04, and after switching to unity desktop, found out, that there's no Ambience theme anymore. Only Adwaita and High contrast are available. :confused:
So my question is - how to enable it again?
Thanks in advance

P.S. i have another ubuntu - 18.04/unity on the same desktop, where an Ambience theme was installed on default , may be it could help somehow

---

### Post by Frogs Hair on 2019-05-11
Try the following.

```
sudo apt install light-themes
```

---

### Post by van hanegen on 2019-05-11
Yes, that was exactly what i needed,
many many thanks! :p

---

### Post by mc4man on 2019-05-11
The best way to add unity in 19.04 is to install the ubuntu-unity-desktop package. It has a dependency on ubuntu-artwork package  which deps on light-themes..

---

