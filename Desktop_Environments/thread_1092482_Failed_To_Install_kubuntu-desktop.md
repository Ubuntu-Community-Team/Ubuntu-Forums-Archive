---
title: "Failed To Install kubuntu-desktop"
date: 2009-03-10
forum: Desktop Environments
---

### Post by woozyking on 2009-03-10
I tried to use

```
sudo apt-get install kubuntu-dekstop
```

But all I get is that it depends on language-selector-qt, which I then get another error message saying language-selector-qt depends on language-selector-common (some version older than the one I've installed now) when I try to install language-selector-qt

Is there any possible solutions than downloading language-selector-qt and older version of language-selector-common as I found on the forum?

Thank you in advance.

---

### Post by taurus on 2009-03-10
Can you post your /etc/apt/sources.list?

```
cat /etc/apt/sources.list
```

---

### Post by Zorael on 2009-03-10
As a small mention, aptitude is better than apt-get at resolving dependencies, so I personally recommend the former for all-around use.

```
$ sudo aptitude install kubuntu-desktop
```

---

### Post by woozyking on 2009-03-10
Thank you both for the help.

I managed to use aptitude to install, with some downgrade and deletion of the packages.

Again thank you both for the great help, I'll update the result once it's done installing.

---

### Post by woozyking on 2009-03-10
I now have KDE 4.1 installed, try to get 2 more things done now:

1. Completely remove all the gnome related stuff, because things like window manager is messed up

2. Upgrade to KDE 4.2.1

Any suggestions?

---

