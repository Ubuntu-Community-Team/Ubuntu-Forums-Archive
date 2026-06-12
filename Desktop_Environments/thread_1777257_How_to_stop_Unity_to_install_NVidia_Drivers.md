---
title: "How to stop Unity to install NVidia Drivers?"
date: 2011-06-07
forum: Desktop Environments
---

### Post by techmad on 2011-06-07
Hey guys,

This is probably very simple but can someone tell me how I stop Unity in order to install graphics drivers?

Thanks!

---

### Post by maverick280857 on 2011-06-07
Log out of Unity to arrive at the login screen (called GDM).

Now press Ctrl + Alt + F1 to go to text mode and type

```
sudo service gdm stop
```

to stop the gdm daemon (this 'stops' GDM).

Install the driver, and reboot the system

```
sudo reboot
```

---

### Post by techmad on 2011-06-07
Great, thanks a million :)

---

