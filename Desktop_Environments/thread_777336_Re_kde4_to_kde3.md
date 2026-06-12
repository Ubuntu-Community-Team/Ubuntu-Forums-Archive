---
title: "Re: kde4 to kde3"
date: 2008-05-01
forum: Desktop Environments
---

### Post by one_ro on 2008-05-01
Hi,

I have a question: is it possible to revert from KDE4 to KDE3?

Adrian

---

### Post by Xiong Chiamiov on 2008-05-02
Most likely you still have KDE3 installed.  When you log in, you should be able to select session type and choose KDE3.  If not, try
```

sudo dpkg-reconfigure kdm

```
and see if you can select kdm, which is the KDE3 version.

If you really feel like it, you can
```

sudo apt-get remove kde4-core

```

---

### Post by one_ro on 2008-05-02
Ah-ha... very useful in case I decide to go back. So far Ill give it a try, and the hopefully improved version 4.1 will be easy to upgrade.

Cheers,
Adrian

---

