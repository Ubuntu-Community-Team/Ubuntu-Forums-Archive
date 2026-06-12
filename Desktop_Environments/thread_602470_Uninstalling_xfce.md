---
title: "Uninstalling xfce"
date: 2007-11-04
forum: Desktop Environments
---

### Post by Zipster90 on 2007-11-04
I recently installed the xubuntu-desktop to try it out, and I decided to uninstall it. However, whenever I go to the login screen, it still shows the xubuntu login screen. Any way to get rid of this? Thanks.

---

### Post by celettu on 2007-11-04
```
sudo dpkg-reconfigure gdm
```

---

### Post by Gremlinzzz on 2007-11-04
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)
:guitar:

---

### Post by Zipster90 on 2007-11-04
None of this worked. The first reply's method wigged out whenever I restarted the session, and the second method appeared to uninstall it but I still get the xubuntu login screen and the option to start an xfce session.

---

### Post by Zipster90 on 2007-11-04
Ok I fixed it. I just went into Synaptic and deleted everything that had to do with xfce. I don't know why the commands didn't do it, though.

---

### Post by TeaSwigger on 2007-11-04
Just a fyi, if you ever want to you can change the usplash with this command:

```
sudo update-alternatives --config usplash-artwork.so
```

Choose the one you want to use, then enter this command:

```
sudo dpkg-reconfigure linux-image-$(uname -r)
```

:)

---

