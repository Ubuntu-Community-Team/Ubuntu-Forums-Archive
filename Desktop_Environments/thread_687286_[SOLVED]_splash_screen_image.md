---
title: "[SOLVED] splash screen image"
date: 2008-02-04
forum: Desktop Environments
---

### Post by Raccoon1400 on 2008-02-04
I downloaded the kubuntu desktop yesterday. Now the splash screen says kubuntu. How do I get it to say ubuntu again, since gnome is still my main desktop?

---

### Post by jan quark on 2008-02-04
if you mean the login screen you can change it in

system > administration > login window

---

### Post by hyperair on 2008-02-04
You problably mean the boot splash. To change it back to ubuntu, you must run..
```

sudo update-alternatives --config usplash-artwork.so

```
Select the one that says "/usr/lib/usplash/usplash-theme-ubuntu.so". Usually, it's the first selection. Then, run this command:
```
sudo update-initramfs -u -k all
```

The next reboot should yield your nice brown ubuntu splash again.

---

### Post by Raccoon1400 on 2008-02-04
Thanks, that worked

---

