---
title: "KDE 'taking over' loading / shutdown screen (NOT login screen)"
date: 2008-08-03
forum: Desktop Environments
---

### Post by Jaded Misanthrope on 2008-08-03
I recently installed KDE to try it out, then uninstalled it and the programs that came with it. However, now when I boot Ubuntu or shut it down, the load / shutdown screen displays Kubuntu instead of Ubuntu. How would I have it display Ubuntu instead, and use the Human colour scheme?

What I mean is the screen looking roughly like this:

[CENTER](circle logo) *BUNTU

[progress bar][/CENTER]

---

### Post by benerivo on 2008-08-03
This screen is named the usplash. Try this line in a terminal```
sudo update-alternatives --config usplash-artwork.so
```If that fails then try [this thread]("http://ubuntuforums.org/showthread.php?t=363519").

---

### Post by coffeecat on 2008-08-03
> **Jaded Misanthrope said:**
> 
[CENTER](circle logo) *BUNTU

[progress bar][/CENTER]


That's called the usplash. Follow steps 3 **and** 4 from [This Community Ubuntu page](https://help.ubuntu.com/community/USplash).

---

