---
title: "Gnome-Shell won't install"
date: 2010-07-22
forum: Desktop Environments
---

### Post by geovino on 2010-07-22
When trying to install gnome-shell I get this error:


sudo apt-get install gnome-shell
davek@davek-laptop:~$ sudo apt-get install gnome-shell
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  gnome-shell: Depends: libgjs0 but it is not going to be installed
E: Broken packages
davek@davek-laptop:~$ 

what would be needed to fix broken packages?
I'm running 10.04 32bit

---

### Post by oldos2er on 2010-07-22
Check System, Administration, Software Sources to make sure you have the universe repository enabled.

To fix broken packages, run ```
sudo apt-get install -f
```

---

### Post by geovino on 2010-07-22
tried that... still doesn't work


davek@davek-laptop:~$ sudo apt-get install -f
[sudo] password for davek: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  mesa-utils gir1.0-pango-1.0 gir1.0-gtk-2.0 gir1.0-clutter-1.0 gir1.0-atk-1.0
  libsox-fmt-base sox gir1.0-mutter-2.28 xserver-xephyr libsox-fmt-alsa
  gir1.0-freedesktop libsox1a gir1.0-glib-2.0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
davek@davek-laptop:~$ sudo apt-get install gnome-shell
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  gnome-shell: Depends: libgjs0 but it is not going to be installed
E: Broken packages
davek@davek-laptop:~$ 

maybe it can't be installed? or somethings missing.

---

### Post by oldos2er on 2010-07-23
You have the universe repository enabled? Run ```
sudo apt-get update
```

---

### Post by geovino on 2010-07-23
> **oldos2er said:**
> You have the universe repository enabled? Run ```
sudo apt-get update
```
I have universe repos checked off. And I have run apt-get update regularly. I'll try again, but somethings missing. I have gnome-shell running on my other PC running fedora 13, so it's not that important to have it on Ubuntu. It will probably be part of the next version 10.10 in October.

---

### Post by oldos2er on 2010-07-23
A little googling turned up this: [https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/555155](https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/555155)

---

### Post by geovino on 2010-07-24
> **oldos2er said:**
> A little googling turned up this: [https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/555155](https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/555155)

...still no fix to the problem... maybe someone will figure out a fix, otherwise I'll wait until version 10.10 comes out.

---

