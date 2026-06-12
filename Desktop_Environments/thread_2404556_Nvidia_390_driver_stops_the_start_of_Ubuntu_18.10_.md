---
title: "Nvidia 390 driver stops the start of Ubuntu 18.10 Cosmic Cutlefish"
date: 2018-10-25
forum: Desktop Environments
---

### Post by diegogermangonzalez on 2018-10-25
After rebooting the system by installing the proprietary Nvidia 390 driver, Ubuntu boot stops displaying the message **Gnome Display Manager O**k.
Sometimes it shows an error in[B] Nvidia Persistence Daemon.
I[/B]n Ubuntu Budgie 18.10 that driver works without problems.
I have tried the recommendations of this tutorial without results

[https://askubuntu.com/questions/1033784/ubuntu-ugrade-17-10-to-18-04-nvidia-black-screen](https://askubuntu.com/questions/1033784/ubuntu-ugrade-17-10-to-18-04-nvidia-black-screen)

---

### Post by $yl9pAR%t on 2018-10-25
If you don't need exactly GDM, install LightDM.
```
sudo apt install lightdm
```

---

### Post by diegogermangonzalez on 2018-10-25
Works. Thanks!

---

### Post by diegogermangonzalez on 2018-10-29
There is an alternative solution
**sudo gedit /etc/gdm3/custom.conf**
Uncomment 
[B]#WaylandEnable=false
[/B]And save the file

---

### Post by $yl9pAR%t on 2018-10-29
Thanks for info. I am curious why Ubuntu 18.04 works without issue with Wayland enabled and why login screen is set by default to Wayland?

---

