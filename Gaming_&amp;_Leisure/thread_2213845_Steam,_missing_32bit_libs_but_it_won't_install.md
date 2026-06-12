---
title: "Steam, missing 32bit libs but it won't install"
date: 2014-03-28
forum: Gaming &amp; Leisure
---

### Post by tamcphan94 on 2014-03-28
Acer c720 chromebook linux via chrubuntu

Steam needs to install these additional packages:     libgl1-mesa-dri:i386, libgl1-mesa-glx:i386, libc6:i386 [sudo] password for user: E: The method driver /usr/lib/apt/methods/https could not be found.

  Reading package lists... Done Building dependency tree
Reading state information... Done Package libc6:i386 is not available, but is referred to by another package. This may mean that the package is missing, has been obsoleted, or is only available from another source However the following packages replace it:   tzdata libdb1-compat locales libc-bin initscripts
  Package libgl1-mesa-glx:i386 is not available, but is referred to by another package. This may mean that the package is missing, has been obsoleted, or is only available from another source
  Package libgl1-mesa-dri:i386 is not available, but is referred to by another package. This may mean that the package is missing, has been obsoleted, or is only available from another source However the following packages replace it:   libgl1-mesa-glx
  W: Duplicate sources.list entry [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable/main amd64 Packages (/var/lib/apt/lists/dl.google.com_linux_chrome_deb_dists_stable_main_binary-amd64_Packages) W: You may want to run apt-get update to correct these problems E: Package 'libgl1-mesa-dri:i386' has no installation candidate E: Package 'libgl1-mesa-glx:i386' has no installation candidate E: Package 'libc6:i386' has no installation candidate Press return to continue:

  When I type in sudo apt-get update: user@chrubuntu:~$ sudo apt-get update [sudo] password for user: E: The method driver /usr/lib/apt/methods/https could not be found.
  When I type in sudo apt-get install ia32-libs user@chrubuntu:~$ sudo apt-get install ia32-libs Reading package lists... Done Building dependency tree
Reading state information... Done Package ia32-libs is not available, but is referred to by another package. This may mean that the package is missing, has been obsoleted, or is only available from another source However the following packages replace it:   lib32z1 lib32ncurses5 lib32bz2-1.0
  W: Duplicate sources.list entry [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable/main amd64 Packages (/var/lib/apt/lists/dl.google.com_linux_chrome_deb_dists_stable_main_binary-amd64_Packages) W: You may want to run apt-get update to correct these problems E: Package 'ia32-libs' has no installation candidate user@chrubuntu:~$

---

### Post by oldrocker99 on 2014-03-28
I had Chrubuntu 13.10 on my Acer C7, and had similar problems, until I reinstalled Chrubuntu using the 12.04 image, which has the ia32-libs metapackage to make Steam installation a snap. 13.10 did away with ia32-libs in favor of multiarch, which didn't work for me. 



After all, 12.04 will be supported for another three years. I use it with MATE for a nice, stable, lightweight desktop.

Later: Found this[http://wiki.phoenixviewer.com/ia32-libs-in-ubuntu-13-10](http://wiki.phoenixviewer.com/ia32-libs-in-ubuntu-13-10). It's a kludge, but it might work.

---

### Post by tamcphan94 on 2014-03-29
> **oldrocker99 said:**
> I had Chrubuntu 13.10 on my Acer C7, and had similar problems, until I reinstalled Chrubuntu using the 12.04 image, which has the ia32-libs metapackage to make Steam installation a snap. 13.10 did away with ia32-libs in favor of multiarch, which didn't work for me. 



After all, 12.04 will be supported for another three years. I use it with MATE for a nice, stable, lightweight desktop.

Later: Found this[http://wiki.phoenixviewer.com/ia32-libs-in-ubuntu-13-10](http://wiki.phoenixviewer.com/ia32-libs-in-ubuntu-13-10). It's a kludge, but it might work.
Didn't work but I before I got the libs in ubuntu 13.10 until I upgraded the SSD and installed new chrubuntu

---

### Post by tamcphan94 on 2014-03-29
I will try to install ubuntu via usb now since acer c720 has seabios let me see if this works.

---

