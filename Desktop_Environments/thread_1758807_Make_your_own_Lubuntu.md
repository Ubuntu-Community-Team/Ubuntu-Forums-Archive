---
title: "Make your own Lubuntu?"
date: 2011-05-15
forum: Desktop Environments
---

### Post by Superpelican12 on 2011-05-15
If you would install Ubuntu/Xubuntu/Kubuntu and then uninstall the Ubuntu-Desktop/Xubuntu-Desktop/Kubuntu-Desktop packages, do you then have to do everything in a kind of terminal (no GUI anymore)? I would make a kind of own Linux distribution by just installing a Ubuntu flavour and then uninstall the 'buntu-desktop package in synaptic. And then type "sudo apt-get install lxde" to install only the bare LXDE core components. To make a own LXDE distribution based on ubuntu.

My question is is this possible? If I uninstall the desktop environment and 'buntu-desktop package will I end up in a non-GUI, terminal-like UI?

Kind Regards,

Superpelican :D

---

### Post by Rubi1200 on 2011-05-15
You might be better off starting from scratch and building your own base install and then adding lxde.

See here for more information:
[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

---

### Post by Superpelican12 on 2011-05-15
I found the ubuntu-minimal package. Which suites perfect for my needs! No GUI or DE installed and the ability to install packages with a CLI. But one problem the ubuntu-minimal package comes in .deb format and I would like to flash it to my usb thumbdrive. Just like any other Linux Distribution.

Does anyone know how to do this?

Kind Regards,

Superpelican :)

---

### Post by Superpelican12 on 2011-05-15
I think I have the right solution, just install any 'buntu flavour and then uninstall all packages accept the ubuntu-mininal package and it' s depencies!

UPDATE:
Found "Mini.iso"s! : [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

---

### Post by I2k4 on 2011-05-15
I'm pretty happy with Lubuntu 10.10 on Live USB, but spent a lot of time uninstalling unwanted software before putting on what I do want.  The mini version might be what I've been looking for.

Update:  Having gone over the "scratch build" instructions it looks like a bit of a wash for time/effort as between building up the mini or stripping down Lubuntu with the package manager.  I might try it as a hobby project on a spare USB drive.

---

### Post by Rubi1200 on 2011-05-15
Just out of curiosity, have you tried following the method in the link I posted?

I haven't used the minimal ISO for a long time, but I was playing around with the method described above.

The results so far are this:

base system + xorg + lxde + chromium browser = 1.2GB

Obviously, there are probably other things I would add, but I am curious to know how the minimal ISO install stacks up in terms of what I found.

Pretty snappy too in terms of speed and stability.

---

### Post by wildmanne39 on 2011-05-16
> **Rubi1200 said:**
> Just out of curiosity, have you tried following the method in the link I posted?

I haven't used the minimal ISO for a long time, but I was playing around with the method described above.

The results so far are this:

base system + xorg + lxde + chromium browser = 1.2GB

Obviously, there are probably other things I would add, but I am curious to know how the minimal ISO install stacks up in terms of what I found.

Pretty snappy too in terms of speed and stability.

Hi, last week I did a minimal install in virtualbox and it only gave me the option of choosing gnome or kde.:)

---

