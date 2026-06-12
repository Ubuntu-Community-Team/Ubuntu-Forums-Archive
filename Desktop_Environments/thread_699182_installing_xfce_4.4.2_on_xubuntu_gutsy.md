---
title: "installing xfce 4.4.2 on xubuntu gutsy?"
date: 2008-02-17
forum: Desktop Environments
---

### Post by syms on 2008-02-17
hi,
i want to upgrade my xfce 4.4.1 version to xfce 4.4.2. how can i do this? updates dont update xfce.

---

### Post by mojoman on 2008-02-17
> **syms said:**
> hi,
i want to upgrade my xfce 4.4.1 version to xfce 4.4.2. how can i do this? updates dont update xfce.

Xfce 4.4.1 is the one that is available in the Ubuntu repositories. 4.4.2 is not available in the backports either so you'll just have to pop by _[www.xfce.org]("www.xfce.org")_ and download the source code and compile it yourself. There is an xfce repository for Debian but I don't know how well it goes down with Ubuntu. It will *probably* work but don't blame me if it doesn't. If you want to try that route, just add the repository to your sources.list and use apt-get to upgrade it.

/mojoman

---

