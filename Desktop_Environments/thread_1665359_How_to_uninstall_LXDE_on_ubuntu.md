---
title: "How to uninstall LXDE on ubuntu"
date: 2011-01-12
forum: Desktop Environments
---

### Post by aldee96 on 2011-01-12
How to remove LXDE from ubuntu 10.10? i've followed the instructions in [http://www.psychocats.net]("http://www.psychocats.net/") to uninstall it, but it's also uninstall several application that i need. do anyone had the way figure it out how?

---

### Post by snowpine on 2011-01-12
You can reinstall the applications you need from the software center or from the terminal with:

```
sudo apt-get install foo
```

where "foo" is the name of the application.

Or, to get back to the default Ubuntu Gnome configuration (if that is your goal):

```
sudo apt-get install ubuntu-desktop
```

---

### Post by aldee96 on 2011-01-13
```
sudo apt-get foo
```

if  use this do i have to re-download them again? so where's the command to fully delete LXDE?

---

### Post by 3Miro on 2011-01-13
> **aldee96 said:**
> ```
sudo apt-get foo
```

if  use this do i have to re-download them again? so where's the command to fully delete LXDE?

If you deleted the applications, then you will have to re-download them.

LXDE is not an applications. It is a collections of applications, if you have followed psycho's instructions, you have removed all of LXDE components. If you think you have deleted something important, you can try to install ubuntu/kubuntu/xubuntu-desktop to get back all of Gnome, KDE or XFCE components (depending on which one you want to use). Note that you can either use the Software Center or Synaptic Package Manager (which might be better of this type of things).

---

