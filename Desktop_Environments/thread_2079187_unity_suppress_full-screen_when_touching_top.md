---
title: "unity: suppress full-screen when touching top?"
date: 2012-11-01
forum: Desktop Environments
---

### Post by iaw4 on 2012-11-01
it's great to have full-screen mode when my app window touches the top bar on a 13" display.  it's less fun on a 30" monitor.  how can I turn this off?

---

### Post by JRV on 2012-11-01
Like this:
```

sudo apt-get install compizconfig-settings-manager

```
Run the program:
```

ccsm

```
Scroll down, at the bottom uncheck "Grid"

---

### Post by iaw4 on 2012-11-01
very cool program.  alas, grid must have been the wrong option, because grid was not enabled.

[does this utility allow me to have the menu items both in the top bar and on the window itself?  I don't think so.]

regards,

/iaw

---

### Post by stinkeye on 2012-11-02
This setting maybe....

---

### Post by jerome1232 on 2012-11-02
Wait, are you actually talking about turning off the Global Menu? The way unity uses the top panel as the applications menu bar which has nothing to do with full-screen vs windowed at all.

---

### Post by stinkeye on 2012-11-02
> **jerome1232 said:**
> Wait, are you actually talking about turning off the Global Menu? The way unity uses the top panel as the applications menu bar which has nothing to do with full-screen vs windowed at all.

Ahh, you may be right.
You can disable the global menu in panel with...
```
echo '[ "$DESKTOP_SESSION" = "ubuntu" ] && unset UBUNTU_MENUPROXY' | sudo tee /etc/X11/Xsession.d/81ubuntu-menu-proxy
```


Enable again...
```
sudo rm /etc/X11/Xsession.d/81ubuntu-menu-proxy
```

---

