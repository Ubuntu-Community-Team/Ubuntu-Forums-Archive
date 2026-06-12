---
title: "Installing Awn error: &quot;broken packages&quot;"
date: 2008-01-20
forum: Desktop Effects &amp; Customization
---

### Post by poo_22 on 2008-01-20
i tried installing avant window navigator following this: [http://www.ubuntugeek.com/howto-install-avant-window-navigator-awn-in-ubuntu-710-gutsy-gibbon.html](http://www.ubuntugeek.com/howto-install-avant-window-navigator-awn-in-ubuntu-710-gutsy-gibbon.html)

the command ```
sudo apt-get install avant-window-navigator-bzr awn-core-applets-bzr

```
returned this:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  avant-window-navigator-bzr: Depends: libawn-bzr but it is not going to be installed
                              Depends: libpango1.0-0 (>= 1.18.3) but 1.18.2-0ubuntu1 is to be installed
                              Depends: libawn-bzr (= 0.2.0-bzr155-1) but it is not going to be installed
  awn-core-applets-bzr: Depends: libawn-bzr but it is not going to be installed
                        Depends: libpango1.0-0 (>= 1.18.3) but 1.18.2-0ubuntu1 is to be installed
                        Depends: libawn-bzr but it is not going to be installed
                        Depends: python-libawn-bzr but it is not going to be installed
E: Broken packages

```

---

### Post by Ub1476 on 2008-01-20
Make sure this is installed:

```
sudo apt-get install build-essential automake1.9 autotools-dev libxdamage-dev libxcomposite-dev libgnome2-common libgnome2-dev libgnome-desktop-dev libgtk2.0-dev libwnck-dev libgconf2-dev libglib2.0-dev libdbus-glib-1-dev python-gtk2-dev python-gconf gnome-common python-dev python-cairo-dev python-gnome2-dev python-gnome2-desktop gnome-panel python-glade2 librsvg2-common

```

---

### Post by poo_22 on 2008-01-20
thx for the reply.
i did that, and no i get similar errors when i tried to install again:
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
The following packages are BROKEN:
  avant-window-navigator-bzr awn-core-applets-bzr libawn-bzr 
The following NEW packages will be automatically installed:
  python-libawn-bzr 
The following NEW packages will be installed:
  python-libawn-bzr 
0 packages upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 2975kB of archives. After unpacking 11.3MB will be used.
The following packages have unmet dependencies:
  awn-core-applets-bzr: Depends: libpango1.0-0 (>= 1.18.3) but 1.18.2-0ubuntu1 is installed.
  avant-window-navigator-bzr: Depends: libpango1.0-0 (>= 1.18.3) but 1.18.2-0ubuntu1 is installed.
  libawn-bzr: Depends: libpango1.0-0 (>= 1.18.3) but 1.18.2-0ubuntu1 is installed.
Resolving dependencies...
Unable to resolve dependencies!  Giving up...
Abort.

```

---

### Post by Shimmy on 2008-01-21
I have the same problem, seems like its broken.

---

### Post by Shimmy on 2008-01-21
Meanwhile it's broken in the repositories, one can compile it from source:

> wget [https://launchpad.net/awn/0.2/0.2.1/+download/avant-window-navigator-0.2.1.tar](https://launchpad.net/awn/0.2/0.2.1/+download/avant-window-navigator-0.2.1.tar)
tar -xvf avant-window-navigator-0.2.1.tar
cd /avant-window-navigator-0.2.1
./configure
make
sudo make install
sudo ldconfig


And to run it:
avant-window-navigator

---

### Post by poo_22 on 2008-01-21
ya, that's what i ended up doing too.

---

### Post by ahervey85 on 2008-01-21
i know this has been answered but i folled this to get awn to work and it did. now i need to know how to uninstall it if anyone can help

---

