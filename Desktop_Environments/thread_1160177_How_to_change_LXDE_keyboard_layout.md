---
title: "How to change LXDE keyboard layout?"
date: 2009-05-15
forum: Desktop Environments
---

### Post by pointyblue on 2009-05-15
In a Xubuntu xfce session my netbook keyboard is reognized as Danish. In lxde its something else and I cant figure out how to change it.

Any ideas?

:)

---

### Post by MobileDev on 2009-05-21
I have the exact same problem! LXDE need some kind of control panel, like what Xfce has. I think it would be a good idea to ransack code from Xfce, trim oof the fat, and integrate it with LXDE.

---

### Post by gpredrag on 2009-05-21
You should set proper keyboard layout in xorg.conf

try: sudo dpkg-reconfigure xserver-xorg

As far as I know LXDE (trying to be lite) uses whatever keyboard layout is set in X.

---

### Post by pointyblue on 2009-05-21
This works:

```
sudo dpkg-reconfigure console-setup
```

:)

---

### Post by deskman on 2011-05-06
Usually xorg.conf is not generated automatically in newer **buntu versions. There is a short video that explains how to set up and switch between keyboard layouts regardless your desktop environement, so it will work allways even after restart: [http://www.youtube.com/watch?v=gzYqREENVVY](http://www.youtube.com/watch?v=gzYqREENVVY)      :)

---

