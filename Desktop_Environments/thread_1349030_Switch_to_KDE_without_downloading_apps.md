---
title: "Switch to KDE without downloading apps?"
date: 2009-12-07
forum: Desktop Environments
---

### Post by jordanae on 2009-12-07
I've been using Ubuntu for years now and for the whole time I've only used Gnome and Xfce DE's. I want to try KDE, but I don't want to download all the apps that come with it. Is it possible to download KDE minus the apps?

---

### Post by lyall on 2009-12-07
see the following link
["http://www.psychocats.net/ubuntu/kde"]()

a great site for other info

good luck and have fun

---

### Post by lisati on 2009-12-07
> **lyall said:**
> see the following link
["http://www.psychocats.net/ubuntu/kde"]()

a great site for other info

good luck and have fun

The link's broken. It should be [http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde) (i.e. without the quotes)

An alternative to the psychocats method is to enter the following command from the terminal:
```

sudo apt-get install kubuntu-desktop

```
Then the next time you're at the logon screen you can choose a KDE session.

---

### Post by lovinglinux on 2009-12-08
> **lisati said:**
> An alternative to the psychocats method is to enter the following command from the terminal:
```

sudo apt-get install kubuntu-desktop

```
Then the next time you're at the logon screen you can choose a KDE session.

That will install all default KDE applications, which is not what the OP wants.

To install KDE without the applications you need *kde-minimal* package instead of *kubuntu-desktop*. You also might want to install *kdeplasma-addons*.

---

### Post by lisati on 2009-12-08
> **lovinglinux said:**
> That will install all default KDE applications, which is not what the OP wants.

To install KDE without the applications you need *kde-minimal* package instead of *kubuntu-desktop*. You also might want to install *kdeplasma-addons*.

Thanks. I stand corrected, and must make a mental note for future. :)

---

