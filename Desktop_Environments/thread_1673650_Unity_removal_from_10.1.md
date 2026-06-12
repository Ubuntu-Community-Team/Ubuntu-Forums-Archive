---
title: "Unity removal from 10.1"
date: 2011-01-22
forum: Desktop Environments
---

### Post by tajreed on 2011-01-22
I inadvertently installed Unity in 10.1. How do I go back to the Classic Desktop?

---

### Post by JOHNNYG713 on 2011-01-22
At your log in window enter your name and password, at the bottom you will or should see sessions click that and boot into Classic or Gnome, I forget just what it says but should be something to that effect !

---

### Post by Krytarik on 2011-01-22
If you want to remove it altogether, look into "/var/log/apt/history.log" what packages has been installed and try to "completely remove" exactly those via Synaptic, it will tell you if other packages are affected by the removal.

---

### Post by tajreed on 2011-01-22
I've tried removing Unity but then get a blank screen. Is it possible that the initial install of Unity wiped out the "Classic Desktop"?

I don't get the log-in option when logging in.

---

### Post by Krytarik on 2011-01-22
> **tajreed said:**
> I've tried removing Unity but then get a blank screen.
Are the packages additionally installed by the Unity install removed now? If not, do it.
After that re-install "ubuntu-desktop":
```
sudo apt-get install --reinstall ubuntu-desktop
```
> **tajreed said:**
> 
Is it possible that the initial install of Unity wiped out the "Classic Desktop"?
I don't think so.

---

### Post by tajreed on 2011-01-22
Thanks everyone, I got it reverted to the U desktop.

---

