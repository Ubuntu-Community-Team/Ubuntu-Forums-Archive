---
title: "Xubuntu"
date: 2006-08-01
forum: Desktop Environments
---

### Post by DetroitBaseball on 2006-08-01
My friend has Xubuntu and wants to uprgade to Ubuntu. I was told you can do this by installing some packages in Package Manager? Is this true, if so what packages?

---

### Post by aysiu on 2006-08-01
It's not an "upgrade"--just an addition. I would recommend using *aptitude* instead of Synaptic Package Manager (makes it easier to remove, should you wish to do so later): ```
sudo aptitude update
sudo aptitude install ubuntu-desktop
```

---

### Post by DetroitBaseball on 2006-08-01
Thanks.

---

### Post by DetroitBaseball on 2006-08-01
Wait, he said the desktop didn't change.

---

### Post by avtolle on 2006-08-01
I believe he can select his desktop at the login screen by selecting the session he wants to use.

---

### Post by matko on 2006-08-01
> **avtolle said:**
> I believe he can select his desktop at the login screen by selecting the session he wants to use.

yes. CtrlAltBackspace and change session.

---

### Post by DetroitBaseball on 2006-08-01
At the login screen he needs to use those keys?

---

### Post by aysiu on 2006-08-01
Control-Alt-Backspace resets the X server, which seems a bit extreme to me.

Just log out and choose.

Illustrations on how to do so can be found here:
[http://www.psychocats.net/ubuntu/gnome.html](http://www.psychocats.net/ubuntu/gnome.html)

---

