---
title: "[SOLVED] Was UBUNTU now EDUBUNTU??? why"
date: 2008-02-08
forum: Desktop Environments
---

### Post by FrancesL on 2008-02-08
Hi, I have no idea what I have installed/downloaded or updated that has changed Ubuntu to now say EDUBUNTU? can someone please assist?

---

### Post by tcommbee on 2008-02-08
what exactly "says" edubuntu? the startup-screen, the about dialog?
you probably installed edubuntu-desktop (which is unlikely to happen by accident)

---

### Post by FrancesL on 2008-02-08
Hi, I get a startup and shutdown screen that now says EDUBUNTU where it did say UBUNUTU

---

### Post by PeterJS on 2008-02-08
That would be uspalsh. To change what image shows up run:
```

sudo update-alternatives --config usplash-artwork.so

```
and then rebuild the boot image with:
```

sudo update-initramfs -u

```

Edit:
Following up on tcommbee's theory I graphed the packages that depend on  edubuntu-artwork-usplash and attached it, it's a pretty short list. You must have installed one of those.

---

### Post by tcommbee on 2008-02-08
you could also install startupmanager to make these changes graphically (under System>Administration>StartUp Manager)

---

### Post by FrancesL on 2008-02-10
Thank you all for your replies and solutions. I followed the suggestions and I am now getting Ubuntu startup/shutdown screen.

---

