---
title: "is it possable to install unity using apt-get?"
date: 2010-10-30
forum: Desktop Environments
---

### Post by goopensorcego on 2010-10-30
hello.

because i want to use unity on my computer without reinstalling ubuntu, i wish to use apt-get to install it. i have heard that it's possable, but i can't figure out how. thanks?

---

### Post by P4man on 2010-10-30
YOu already posted it, basically.

```
sudo apt-get install unity
```

Then log out, and in the GDM login screen select your user and then at the bottom select "netbook interface".

---

### Post by kerry_s on 2010-10-30
> **goopensorcego said:**
> hello.

because i want to use unity on my computer without reinstalling ubuntu, i wish to use apt-get to install it. i have heard that it's possable, but i can't figure out how. thanks?

```
sudo apt-get install ubuntu-netbook
```

you want to make sure you get everything.
unity's mutter is 3d accelerated, don't bother if your vid card can't do that.

---

