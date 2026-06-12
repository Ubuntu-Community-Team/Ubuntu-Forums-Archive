---
title: "Is it possible,just a base system?"
date: 2006-02-28
forum: Desktop Environments
---

### Post by Tha1 on 2006-02-28
Hey,just wanna ask this:
Is it possible to just install a base system from the CD? It's just that there is so much thing in a normal install that is installed that i wanna try to install manually without trimming the normal installation. Is it possible?

---

### Post by scorcher on 2006-02-28
Yes, it is possible.

When the first screen of the installer CD comes up and asks you to press Enter, type 'server' and then press Enter.

---

### Post by chele on 2006-02-28
Yes.```
boot: server
```

---

### Post by Tha1 on 2006-02-28
Thanks, you guys rock!!\\:D/ \\:D/

---

### Post by az on 2006-02-28
You will not get a graphical system with this.

You will reboot to a command prompt.  That's normal.

To install stuf after that, you will have to use apt.

sudo apt-get install x-window-system-core xterm gdm ....


You would be best to install the ubunutu-destop package and that will bring everything in.  Then remove stuff...

---

### Post by Tha1 on 2006-03-01
Thanks, but I'd really like to install things from a base system. i don't mind messing with the CLI (i doone it already with another distro),and i found it very educational(and fun,too).By the way, 2 questions:
What's the name of the package for Gnome(base)?
Did Ubuntu already moved to X.Org?

---

### Post by taurus on 2006-03-01
To install Gnome, 

```

sudo apt-get install ubuntu-desktop

```

Ubuntu has been using Xorg for a while now!!!  In fact, I think almost every Linux distro is using Xorg...

---

### Post by scorcher on 2006-03-01
If you install the ubuntu-desktop package you will get all the packages from the default full installation, not just gnome.

If you want just the basic gnome stuff, install
```
gnome-core
```

And for all the gnome packages, install
```
gnome-desktop-environment
```

---

### Post by az on 2006-03-01
[QUOTE=Tha1]
What's the name of the package for Gnome(base)?
Did Ubuntu already moved to X.Org?[/QUOTE]
sudo apt-get install gnome

sudo apt-get install x-window-system-core

A neat basic system is had with

sudo apt-ge tinstall x-window-system-core xterm gdm icewm menu synaptic mozilla-firefox

(Just pick the icewm session before you log into gdm the first time, it default to gnome and there will be a lot of stuff missing if you just ran that from a server install.)

---

