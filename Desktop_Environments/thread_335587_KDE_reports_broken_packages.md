---
title: "KDE reports broken packages"
date: 2007-01-10
forum: Desktop Environments
---

### Post by DarkNemesis618 on 2007-01-10
I have ubuntu 6.10 installed on my system. works fine under gnome (my preferred DE) but I want to monkey around with KDE as well.  However when I try to install KDE, i get this message:

Here's my command:
```
sudo apt-get install kde
```

And this is what it gives me
```
The following packages have unmet dependencies:
  kde: Depends: kdemultimedia (>= 4:3.4.3) but it is not going to be installed
E: Broken packages

```

Any ideas?

---

### Post by kebes on 2007-01-10
To install KDE on Ubuntu, use the "kubuntu-desktop" package, which has all dependencies built into it:

sudo aptitude install kubuntu-desktop

---

### Post by DarkNemesis618 on 2007-01-10
Thanks, that worked.

---

