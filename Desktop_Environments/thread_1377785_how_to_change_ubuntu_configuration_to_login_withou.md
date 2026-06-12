---
title: "how to change ubuntu configuration to login without login and pass (from recovry more"
date: 2010-01-10
forum: Desktop Environments
---

### Post by darkmode on 2010-01-10
how to change ubuntu configuration to login without login and pass (from recovry mode
plz help as soon as posible

---

### Post by benerivo on 2010-01-10
Try```
sudo nano /etc/gdm/custom.conf
```and changing the daemon section (or adding if it doesn't exist) to be```
[daemon]
AutomaticLoginEnable=true
AutomaticLogin=ben
```

---

