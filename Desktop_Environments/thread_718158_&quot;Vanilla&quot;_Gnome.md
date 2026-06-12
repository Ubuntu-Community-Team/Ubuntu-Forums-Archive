---
title: "&quot;Vanilla&quot; Gnome?"
date: 2008-03-07
forum: Desktop Environments
---

### Post by CM Xtasy on 2008-03-07
Is there a way I can get Ubuntu to have a "vanilla" gnome?  I enjoyed the speed of Debian, and didn't mind the look of it.  I'd still like an auto-installer for packages and such.  Is this possible?

---

### Post by boeing777 on 2008-03-07
you could install Ubuntu Server edition which has not interface? just command line

---

### Post by CM Xtasy on 2008-03-07
> **boeing777 said:**
> you could install Ubuntu Server edition which has not interface? just command line

Does it come with an automatic package installer?  I like GUI lol.  Debian couldnt automatically install .debs for some reason :|

---

### Post by boeing777 on 2008-03-07
all the softwares i download comes in .BIN or .DEB which is automatic installation.  Sometimes depending on the software, there's graphical installer.

always, you can always install more package using Synpatic Package Manager, it's all automatic

---

### Post by ung/xunil on 2008-03-07
> **CM Xtasy said:**
> Is there a way I can get Ubuntu to have a "vanilla" gnome?  I enjoyed the speed of Debian, and didn't mind the look of it.  I'd still like an auto-installer for packages and such.  Is this possible?

If you want to install Ubuntu without the package "[ubuntu-desktop]("http://packages.ubuntu.com/gutsy/ubuntu-desktop")" ("tasksel install ubuntu-desktop"), which is installed by default with a Ubuntu Desktop CD or with an Alternate one, and which installs gnome+openoffice+evolution+all_the_ubuntu_stuff, and just want to install a base "[gnome-core]("http://packages.ubuntu.com/gutsy/gnome-core")" package that just installs Gnome, without anything else, you could do the following:

- Boing777 said to use a Ubuntu Server CD to install a command line system (just a Ubuntu/Debian GNU/Linux system) and then install the GUI over it, but that would install a "[linux-image-server]("http://packages.ubuntu.com/gutsy/linux-image-server")" kernel, not the "[linux-image-generic]("http://packages.ubuntu.com/gutsy/linux-image-generic")". But there is a way.
- To install the just the "generic" kernel (without "[ubuntu-desktop]("http://packages.ubuntu.com/gutsy/ubuntu-desktop")", just "[ubuntu-standard]("http://packages.ubuntu.com/gutsy/ubuntu-standard")") use an Alternate CD (not the liveCD) and on the first menu choose "Install a command line system" (or something like that).
- After setting up partitions, install options and GRUB, you will reboot to a command line system.
- Install just the packages that you want:"[gdm]("http://packages.ubuntu.com/gutsy/gdm")", "[gnome-core]("http://packages.ubuntu.com/gutsy/gnome-core")" and "[xserver-xorg]("http://packages.ubuntu.com/gutsy/xserver-xorg")".
```
sudo apt-get install gdm gnome-core xserver-xorg
```
This will install +250 MB of packages (+600 MB of disk space). Select some valid and securely-known-to-work resolutions for Xorg server. Reboot again.
```
sudo reboot
```
Ubuntu should restart with Xorg server working, and if you login you will get a Gnome desktop without any themes, evolution, openoffice, gimp, etc. Just bare Gnome. Install all the rest as you wish.

I think that this will do what you want. Did not tested it, but it should work. Good luck.

PS: Synaptic is included in "gnome-core".

---

