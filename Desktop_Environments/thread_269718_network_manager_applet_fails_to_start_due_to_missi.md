---
title: "network manager applet fails to start due to missing icons"
date: 2006-10-02
forum: Desktop Environments
---

### Post by ramiro on 2006-10-02
The gnome network manager applet (on a fresh install) doesn't work, complaining about missing icons. This was done by installing with the desktop CD and then installing the latest network-manager-gnome package from the Internet. The required panel icons were not installed and it wouldn't start unless I manually copied the icons over. 

This occurred on both dapper and edgy.

I filed a [launchpad bug]("https://launchpad.net/distros/ubuntu/+source/network-manager/+bug/59740") but it hasn't got a response. Has anyone else had this issue?

---

### Post by miobio on 2006-10-04
Same problem here!!!

Where did you find the icon??

Can you upload it here or tell me where i can find it please :-)

---

### Post by clobs on 2006-10-05
Hi.

If you get an error message like this: "*The NetworkManager applet could not find some required resources. It cannot continue*" Then the solution, should be to type in a terminal:

```
sudo gtk-update-icon-cache -f /usr/share/icons/hicolor
```

According to this page that is on french:
[http://doc.ubuntu-fr.org/applications/network_manager](http://doc.ubuntu-fr.org/applications/network_manager)

I haven't test it yet, because I don't have this problem but I guess it should solve the problem.

Good luck.

---

