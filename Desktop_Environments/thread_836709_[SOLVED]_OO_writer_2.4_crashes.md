---
title: "[SOLVED] OO writer 2.4 crashes"
date: 2008-06-21
forum: Desktop Environments
---

### Post by dansan on 2008-06-21
After installing 8.04, OO Writer 2.4 worked fine, but after recent updates, I can't open it. It just crashes. I don't know which update it was since I don't use it daily.

This only happens with Writer. The other OO programs work normally. Anyone else experiencing this? Did you fix it?

---

### Post by p_quarles on 2008-06-21
What, if any, feedback do you get from the terminal? If you haven't attempted to launch it from there yet, you can do so by typing:
```
oowriter
```

---

### Post by dansan on 2008-06-22
> **p_quarles said:**
> What, if any, feedback do you get from the terminal? If you haven't attempted to launch it from there yet, you can do so by typing:
```
oowriter
```

There is no additional feedback; writer behaves exactly the same. This time I took screenshots to show what it does. View from left to right.

Furthermore, it makes no difference removing and reinstalling writer, either with Synaptic or Aptitude. The reinstalled version behaves exactly as the removed one.

***
The crashing only happens when a new document is being created.

I just discovered that Writer will open an existing document, of course groaning about the last crash and document it cannot recover. Then it opens the existing document.

P Quarles, hopefully, you'll figure out what's going on and how to stop it.

---

### Post by jflassche on 2008-06-29
Hi dansan,

I experienced the same problem running Ubuntu 8.04. The solution (at least for now) is to uninstall openoffice.org-kde.

```
sudo apt-get autoremove --purge openoffice.org-kde
```

This seems to be the package that spoils everything! ;-)

---

### Post by dansan on 2008-07-01
Hey jflassche,

I'll give this a try. Thanks for the tip.


> **jflassche said:**
> Hi dansan,

I experienced the same problem running Ubuntu 8.04. The solution (at least for now) is to uninstall openoffice.org-kde.

```
sudo apt-get autoremove --purge openoffice.org-kde
```

This seems to be the package that spoils everything! ;-)

---

### Post by jflassche on 2008-07-03
The package (openoffice.org-kde) was recently updated. You should be able to (safely) reinstall it!

---

### Post by dansan on 2008-07-04
Thanks for this update. The same day as it came, the update service included openoffice.org-kde in its 43 offerings, and after installation, the problem was fixed.

:) Ubuntu gets another 10!

---

