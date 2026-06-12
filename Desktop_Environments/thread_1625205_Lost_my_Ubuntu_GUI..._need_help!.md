---
title: "Lost my Ubuntu GUI... need help!"
date: 2010-11-18
forum: Desktop Environments
---

### Post by bradRNstyle on 2010-11-18
I am using Ubuntu v10.04 (Ultimate Linux) with the Gnome desktop environment.  I tried another desktop environment (it comes with many) and it failed.  Now I only boot to a grey screen and can't set it back to Gnome (or any) environment.  I can boot to a command line in recovery mode, but how can I set my GUI back to Gnome (or KDE) from the command line?  Please help I am 100% Linux and stuck with no computer in the middle of the semester at medical school!

---

### Post by tom4everitt on 2010-11-19
To launch Gnome from command line, try:

```

start gdm

```
(after you've logged in, of course).

If that works, you can set your preferred login manager in System->Administration->Login Screen

---

### Post by tom4everitt on 2010-11-19
If that fails, you can also try to reinstall ubuntu-desktop. Hopefully it will ask you if you want to set the login manager during install. To reinstall ubuntu-desktop, do:

```

sudo apt-get remove ubuntu-desktop
sudo apt-get install ubuntu-desktop

```

---

### Post by bradRNstyle on 2010-12-11
thanks for the help. its working again.

---

