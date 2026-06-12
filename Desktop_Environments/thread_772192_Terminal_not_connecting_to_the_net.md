---
title: "Terminal not connecting to the net"
date: 2008-04-28
forum: Desktop Environments
---

### Post by thevoidreturns on 2008-04-28
Hello,
    I'm trying to solve one problem but in doing so discovered another problem.

My problem is that I did an upgrade to Hardy Heron and I'm having a problem with Xorg. When booting I have a screen that flickers just as the login screen tries to display, but fails. I know this has to do with my graphics driver. I have tried setting the driver as Vesa in my xorg.conf file and also replaced the xorg.conf with xorg.conf.old my backup before the upgrade, it fails. Last night I did get the system up and running but the performance of the system was very poor (ie compiz running extremely slow with its effects).

After reading through the forums I would like to try and install Envyng by the means of apt-get install envyng-gtk. Unfortunately, while in the terminal both the recovery terminal and by accessing through alt+ctrl+f2 the terminal is unable to connect to the router and ultimately the net. I've tried ping unable to ping the  router but is able to ping the loopback address.

Can someone give me a little hint of where I am going wrong or how to get my system back up and running as it was before I did the upgrade?

Thanks
Adam

---

### Post by ryanhaigh on 2008-04-28
What type of network are you on, if it is wired you might want to try:
```

sudo ifconfig eth0 up
sudo dhclient eth0

```

---

### Post by thevoidreturns on 2008-04-28
Up and running thanks :)

---

