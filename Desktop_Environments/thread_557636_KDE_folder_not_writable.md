---
title: "KDE folder not writable"
date: 2007-09-22
forum: Desktop Environments
---

### Post by Kundalinux on 2007-09-22
Even though I am the administrator my KDE folder seems to be not writable so I can't run Amarok. When I start the program it gives me a series of errors. My KDE folder in “home” looks red with an “X” on it. I never had this problem on previous Ubuntu installations. I am quite lost. Pleaase help

---

### Post by mlissner on 2007-09-22
Do this, and tell us what you get:
```
ls -d /home/*
```

---

### Post by Kundalinux on 2007-09-25
> **mlissner said:**
> Do this, and tell us what you get:
```
ls -d /home/*
```

I get this:

(user)@(user)-desktop:~$ ls -d /home/*
/home/(user)

---

### Post by Waappu on 2007-09-25
Hi

You can fix permission typing in terminal
```
chown -R masterpix ~/.kde
```

---

### Post by Kundalinux on 2007-09-25
> **Waappu said:**
> Hi

You can fix permission typing in terminal
```
chown -R masterpix ~/.kde
```

Thanks a lot!
But I get: "Permission denied"

---

### Post by Waappu on 2007-09-25
Hi
try this
```
sudo chown -R masterpix ~/.kde
```

---

### Post by Kundalinux on 2007-09-25
> **Waappu said:**
> Hi
try this
```
sudo chown -R masterpix ~/.kde
```

Hey you rock! My KDE folder is unlocked and Amarok seems to be working.
Big THANKS!

---

