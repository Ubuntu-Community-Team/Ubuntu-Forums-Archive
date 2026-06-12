---
title: "Making kernel image need help"
date: 2009-04-29
forum: General Help
---

### Post by Silvr2008 on 2009-04-29
Please forgive me for having such a newbish question but I have never compiled my own kernel. I have been googling around and trying to figure this out on my own and feel saturated with information at this point.

I am trying to upgrade my kernel to 2.6.28.9 with the grsec patch. I am getting the 2.6.28.9 kernel from kernel.org I have successfully done this with:

cp /boot/2.6.28-11-generic .config
make menuconfig
make
make modules
make install
make modules_install

I get some errors on startup relating to apparmor and the klogd. I googled around and found that apparmor is its own module to I would need to add it to the build. So I found the linux-backports-modules-2.6.28 2.6.28-11.12 at launchpad and created a symlink in /usr/src called modules pointing to the 3 folders that untarred.

I would like to make a package with this configuration that I can move around and install on other computers so now I am doing:

fakeroot make-kpkg
fakeroot make-kpkg –-initrd kernel_image kernel_headers modules_image

Regardless of whether apparmor will work with grsec or not. I would like to know if I am doing this correctly. Those are the modules source that I will need to make a package and install with Ubuntu right? They do need to be in /usr/src/modules right? There was not a folder called modules in there before. You would not need to normally do modules_image when making a kpkg because it already makes any modules that are in the .config right?

When I am doing the build I get:

make[1]: Entering directory `/usr/src/ubuntu-jaunty-lbm'
make[1]: *** No rule to make target `kdist_image'.  Stop.
make[1]: Leaving directory `/usr/src/ubuntu-jaunty-lbm'
Module /usr/src/modules failed.

Any help with this would be greatly appreciated!

---

