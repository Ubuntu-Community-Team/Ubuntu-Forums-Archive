---
title: "Enable nvidia drivers from recovery mode"
date: 2008-04-27
forum: Desktop Environments
---

### Post by gavos on 2008-04-27
Hello guys, i just disabled restricted drivers for my nvidia video card and ubuntu gives me white screen everey time i login. I can only boot normally from recovery mode where i tried many setting at xorg but nothing happens. Is there i way to enable again nvidia restricted drivers from recovery mode? Thank so much for your help..

---

### Post by quintok on 2008-04-27
I assume that means you uninstalled the driver... so here's how to install it from the command line (or from recovery mode using Terminal)

> sudo apt-get install nvidia-glx-new
sudo nvidia-xconfig


Note this does mean you were using nvidia-glx-new, there are a few versions depending what 3d card you were using.  Geforce 4 and up require nvidia-glx-new.  Geforce 3 and below use the package called 'nvidia-glx'

If you've never used the terminal before 'sudo' will ask you for a password, it's the same as your main accounts password.

---

