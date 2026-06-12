---
title: "slab from svn: no package NetworkManager found"
date: 2007-12-18
forum: Desktop Environments
---

### Post by ayampanggang on 2007-12-18
i tried to install the slab menu / gnome-main-menu from svn but when i ran autogen.sh it exits with error:
> No package 'NetworkManager' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables MAIN_MENU_CFLAGS
and MAIN_MENU_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

the strange thing is that NetworkManager is a package which comes from ubuntu right? and it is already installed here. the nm-applet icon appears and when i type whatis NetworkManager it outputs "NetworkManager (1)   - network management daemon" so it should be installed well right?

so what can makes this error?

thank you so much :)

---

### Post by Nano Geek on 2007-12-18
Try installing this:```
sudo apt-get install network-manager-dev
```and run the ./configure again.

---

