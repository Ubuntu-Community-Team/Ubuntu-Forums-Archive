---
title: "Help totally re-doing an XFCE installation."
date: 2008-02-27
forum: Desktop Environments
---

### Post by SomeGuyDude on 2008-02-27
I installed XFCE4 via Synaptic, and loved it. But somehow, when I used AWN, something went terribly wrong and right-click stopped giving me the XFCE menu, it loaded up with all the wrong settings, etc.

Is there ANY way to get a totally clean install of XFCE? Nothing I do works. I've uninstalled and reinstalled a few times, and every time it's like it stores my settings somewhere, but I have no idea where.

Help!

---

### Post by p_quarles on 2008-02-27
It's storing them in multiple directories inside your home folder. The absolute easiest way to fix this would be to create a new user:
```
sudo useradd -m *name*
```The "-m" option automatically generates a new home folder with the same name, and the system will create the default configuration files as you start each application. 

You can also go through your current user's home directory and manually remove each config directory, but that will be a lot more work.

---

### Post by tgalati4 on 2008-02-27
Give Linux Mint 4 XFCE a spin.  New operating system in 18 minutes.

---

### Post by SomeGuyDude on 2008-02-27
What I ended up doing was doing a desktop search, including hidden files, and deleted anything with XFCE that wasn't part of my icon set. That seems to have done the trick.

I will take a look at Mint 4 XFCE, however. Have you tried it?

---

### Post by tgalati4 on 2008-02-27
I've used Linux Mint 4 XFCE on several machines from older PIII, 500 MHz to 2.8 GHz Core 2 Duo's.  Runs well on older or newer machines.  Since it has the codecs already installed, it requires less fiddling for new users.  Also Mint Update hides kernel and xorg updates from users (unless you change default settings) so you can use your setup longer before hosing it.

Ubuntu tends to push all updates including kernel and xorg, both which can break an installation.  This frustrates new users because one minute their system was working, update, then wham, not working.  New users often have no idea how to roll back an update to get back to a working system.

Since Mint is based on Ubuntu code base, it's easy to use for Ubuntu users.  The fixes you find in these forums tend to work in Mint as well.

---

### Post by exneo002 on 2008-02-27
sudo apt-get remove xubuntu-desktop 
sudo apt-get install xubuntu-desktop 
will remove and reinstall

---

### Post by p_quarles on 2008-02-27
> **exneo002 said:**
> sudo apt-get remove xubuntu-desktop 
sudo apt-get install xubuntu-desktop 
will remove and reinstall
No, actually it will not. xubuntu-desktop is a "dummy" package, meaning that it does not contain any actual binary code, but is instead a list of dependencies. Installing it will fetch all the dependencies. Uninstalling it will do nothing.

---

