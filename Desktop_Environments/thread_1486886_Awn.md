---
title: "Awn?"
date: 2010-05-18
forum: Desktop Environments
---

### Post by joek71 on 2010-05-18
Hi guys

I noticed that AWN does not work with this newest version of Ubuntu, is there a work around or fix coming up anytime soon?

Thanks

---

### Post by Cathhsmom on 2010-05-18
My Awn is working in the newest 10.04.  What is happening with your Awn?

---

### Post by joek71 on 2010-05-18
I cant install it at all, i  get errors

---

### Post by joek71 on 2010-05-18
When i do install using the terminal i get this:

The following packages have unmet dependencies:
  avant-window-navigator-bzr: Depends: libawn0-bzr (= 0.3.1.bzr489.3~hardy) but it is not going to be installed
                              Depends: libgnome-desktop-2 (>= 1:2.22) but it is not installable
                              Depends: python-gnome2-extras but it is not installable
  awn-core-applets-bzr: Depends: libawn0-bzr but it is not going to be installed
                        Depends: libffi4 but it is not installable
                        Depends: libgnome-desktop-2 (>= 1:2.22) but it is not installable
                        Depends: python2.5 (>= 2.5) but it is not installable
                        Recommends: python-awn-bzr but it is not going to be installed
                        Recommends: python-libgmail but it is not installable
                        Recommends: vala-awn-bzr but it is not installable
  awn-manager-bzr: Depends: python-awn-bzr but it is not going to be installed

---

### Post by Pauly BC on 2010-05-18
+1

---

### Post by portentum on 2010-05-18
Can you share your sources.list?

I see you're trying to install avant-window-navigator-bzr and not [avant-window-navigator]("http://packages.ubuntu.com/lucid/avant-window-navigator") (the package in the official repos) and it's trying to grab a dependency from Hardy...

---

