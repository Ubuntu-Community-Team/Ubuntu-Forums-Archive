---
title: "How do I get Fedora 7 fonts in Feisty?"
date: 2007-07-01
forum: Desktop Environments
---

### Post by lancest on 2007-07-01
I like the desktop fonts better in Fedora 7. They look clearer at size 10 gnome (default) than in Ubuntu Feisty. How do i get them in Feisty?  Is it because of Fedora 7 having the newest Xorg?

---

### Post by coffeecat on 2007-07-02
It may because the font hinting is set up differently in Fedora. Have you tried enabling autohinting in Feisty? Try:

```
sudo dpkg-reconfigure fontconfig-config
```Answer yes to autohinting and accept the defaults to the other two questions. You have to restart the xserver to see the difference. If you don't like it, then simply run that command again and switch autohinting off.

Although [this wiki page is for Gentoo]("http://gentoo-wiki.com/HOWTO_Xorg_and_Fonts"), it has some useful information about font hinting.

---

