---
title: "Help me. im hopeless."
date: 2008-01-29
forum: Desktop Effects &amp; Customization
---

### Post by SuperGO on 2008-01-29
im just trying to install and run beryl and compiz on mt VAIO VGN-N365E running ubuntu 7.10  and i cant seem to do it. i have been trying for days and any help would be greatly appreciated.

when i type in 'compiz' to my terminal i get :

casey@Omoikane:~$ deb [http://ppa.launchpad.net/amaranth/ubuntu](http://ppa.launchpad.net/amaranth/ubuntu) feisty main universe 

bash: deb: command not found
casey@Omoikane:~$ deb-src [http://ppa.launchpad.net/amaranth/ubuntu](http://ppa.launchpad.net/amaranth/ubuntu) feisty main universe
bash: deb-src: command not found
casey@Omoikane:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:27a2 (rev 03) (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1024x768) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

---

### Post by aysiu on 2008-01-29
```
deb http://ppa.launchpad.net/amaranth/ubuntu feisty main universe 
``` is not a command to put into the terminal. It is a software source to be put into the /etc/apt/sources.list file.

That said, I've never heard of this ppa.launchpad.net source before, and I don't believe it's needed in order to run Beryl/Compiz.

Try this instead:
[http://psychocats.net/ubuntu/desktopeffects](http://psychocats.net/ubuntu/desktopeffects)

---

