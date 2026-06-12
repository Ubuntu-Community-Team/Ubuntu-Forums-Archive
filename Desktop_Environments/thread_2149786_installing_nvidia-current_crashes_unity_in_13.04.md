---
title: "installing nvidia-current crashes unity in 13.04"
date: 2013-05-29
forum: Desktop Environments
---

### Post by hydrodog on 2013-05-29
I foolishly tried to install nvidia-current and now unity crashes.  I can still see this browser, but I can't switch between windows or control the stacking order.  There are no window borders.

I uninstalled nvidia-current but nothing works.  How do I get back to the state the system was before the install of that package?

---

### Post by deadflowr on 2013-05-30
When you uninstalled nvidia-currents, you need to move or remove the xorg.conf file as well.

```
sudo rm /etc/X11/xorg.conf
```

Then reboot.

If unity still doesn't load, try resetting it with the procedure here

[http://www.omgubuntu.co.uk/2013/04/how-to-reset-unity-compiz-in-ubuntu-12-10-and-13-04](http://www.omgubuntu.co.uk/2013/04/how-to-reset-unity-compiz-in-ubuntu-12-10-and-13-04)

---

### Post by hydrodog on 2013-05-30
There is no file /etc/X11/xorg.conf

and resetting has no effect.

I just looked at syslog:
sudo cat /var/log/syslog | grep NV

and nvidia is "tainting the kernel"

HOW do I get rid of that poison pill?  Isn't there any clean way to back out?

---

### Post by Frogs Hair on 2013-05-30
Did you revert to the default nouveau driver by way of Software & Updates or simply remove Nvidia current ?

---

