---
title: "default gateway device"
date: 2006-05-25
forum: Desktop Environments
---

### Post by kasemodz on 2006-05-25
hi, I have 2 nics going to different routers. I want eth0 to be my default gateway device (getting internet and stuff). However, when I go to network configuration on gnome, I somehow cannot change it to eth0. I can select it and    press ok, but when i go back to window, it selects eth2. Any manual way to fix that?

---

### Post by halfvolle melk on 2006-05-25
You could try to edit /etc/network/interfaces.
```
sudo vi /etc/network/interfaces
```
It allows you to set a gateway for each nic.

---

