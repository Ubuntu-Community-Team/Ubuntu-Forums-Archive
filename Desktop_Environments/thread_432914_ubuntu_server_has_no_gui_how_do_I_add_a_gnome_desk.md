---
title: "ubuntu server has no gui? how do I add a gnome desktop?"
date: 2007-05-04
forum: Desktop Environments
---

### Post by drokmed on 2007-05-04
I just installed the Dapper 6.06.1 server (amd64), and have a text-login.

I'd like to install a complete gnome desktop:

sudo apt-get install ???????

Thanks!

---

### Post by ohgod on 2007-05-04
sudo apt-get install ubuntu-desktop (for gnome)
-or-
sudo apt-get install kubuntu-desktop (kde)
-or-
sudo apt-get install xubuntu-desktop (xfce)

---

### Post by drokmed on 2007-05-04
thanks :)

---

### Post by phoenix24x on 2007-09-19
how do i launch it?

---

### Post by Lord Illidan on 2007-09-19
Did you type the command into the prompt?

```
sudo apt-get install ubuntu-desktop
```?

---

### Post by bigken on 2007-09-19
startx

---

### Post by dcstar on 2007-09-20
> **phoenix24x said:**
> how do i launch it?

```
sudo /etc/init.d/gdm restart
```

---

### Post by rsambuca on 2007-09-20
If you don't want all of the ubuntu extras, you can also just install gnome-core, or gnome-desktop-environment.

---

