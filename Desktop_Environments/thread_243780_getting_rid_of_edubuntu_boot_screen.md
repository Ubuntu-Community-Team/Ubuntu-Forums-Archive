---
title: "getting rid of edubuntu boot screen"
date: 2006-08-25
forum: Desktop Environments
---

### Post by damocles on 2006-08-25
Hi all, can somebody tell me how can I change the boot screen (not GRUB boot screen but ubuntu boot screen with all the loading info etc.).  For some reason I installed edubuntu wallpapers an other stuff and right now I am stuck with edubuntu boot screen..

Thanks...

---

### Post by damocles on 2006-08-25
H

---

### Post by Metacarpal on 2006-08-25
Hi Damocles,

Open a Terminal (Applications > Accessories > Terminal) and type:

```
sudo aptitude remove edubuntu-artwork-usplash
```

It'll ask for a password; give it the same password you use to login.  Then:

```
sudo aptitude update
```
followed by
```
sudo aptitude reinstall usplash
```

That should fix you right up.

---

