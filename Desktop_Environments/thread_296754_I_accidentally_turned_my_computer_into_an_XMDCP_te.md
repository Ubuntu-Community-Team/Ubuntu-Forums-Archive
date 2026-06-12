---
title: "I accidentally turned my computer into an XMDCP terminal."
date: 2006-11-10
forum: Desktop Environments
---

### Post by heycarsten on 2006-11-10
I accidentally turned my computer into an XMDCP terminal. When I boot up I just get a login that has a list of XMDCP servers which I can then log in to. How do I get the login to go back to the default gdm one? I'm running Ubuntu 6 Server with the ubuntu-desktop apt-getted.

This all stemmed from me trying to figure out a way to get the xserver to shut down. I was messing with some settings in which it said some warning about this exact situation happening... LOL... Oh well, I can still get access to the system via SSH from my Mac, and everything still runs fine, I've been using it as a LAMP dev server for weeks with no problems.

If anyone can help me fix this via the terminal and SSH I would greatly appreciate it!

---

### Post by lazyart on 2006-11-10
Press F10 and change it to Gnome.

---

### Post by taurus on 2006-11-10
Maybe you just need to start gdm again!

```
sudo /etc/init.d/gdm start
```

---

