---
title: "Installed xfce - how to I auto-start it at startup?"
date: 2009-05-16
forum: Desktop Environments
---

### Post by Nixie Pixel on 2009-05-16
Hi, I have installed xfce4 as a light-weight desktop for my Ubuntu Server.  This is a real noobish question, but can someone please tell me how I start the desktop automatically on boot?  Is there a file I can edit somewhere that will start xfce at startup?

Thanks!

---

### Post by taurus on 2009-05-16
I believe XFce4 uses xdm as GUI login screen so make sure you have installed that too.  Then, run

```
sudo /etc/init.d/xdm start
```

---

### Post by Nixie Pixel on 2009-05-16
Thank you - just to be clear, this will automatically load xfce each time I reboot the server (which hopefully won't be that often)?

---

### Post by taurus on 2009-05-16
Did you install the xubuntu-desktop package?

---

### Post by Nixie Pixel on 2009-05-16
No, just xfce4, and now xdm.

---

### Post by Brandon Williams on 2009-05-17
That _should_ be enough, provided that either /usr/bin/x-session-manager or /usr/bin/x-window-manager points to something useful for starting an XFCE session. I think that this will be true after installing xfce4 and its dependencies. If not, you will want to create a ~/.xsession file to handle initializing the session for you.

---

