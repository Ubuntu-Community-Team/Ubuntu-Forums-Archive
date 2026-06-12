---
title: "Jaunty 64 X-plane install, Segmentation fault"
date: 2009-05-09
forum: Gaming &amp; Leisure
---

### Post by dhysk on 2009-05-09
I'm trying to install x-plane off of the official DVD.  I have obtained all the libs required in the /lib32/ however when i try to run the Installer_Linux i get a 'Segmentation fault' and nothing happens.  Any ideas?

This is my first go at linux64.

---

### Post by dhysk on 2009-05-11
YA, finally. To initially get to the segmentation fault I made sure I had all the libs listed in this forum [http://forums.x-plane.org/index.php?showtopic=34824](http://forums.x-plane.org/index.php?showtopic=34824).  For me after installing the Nvidia driver 180.51 all I had to do was create a sim link for openal.so.0 pointing to openal.so.1.  After that as stated above I would get a segmentation fault once I tried to run the Installer_Linux off of the DVD.

The problem was derived from my own stupidity.  When installing the Nvidia drivers and saying yes to install the 32bit libs I would get an error that said something like the following:

unable to perform runtime configuration check for library libGL.so.1

Everything else worked however once I installed the build-essential packedges and re-ran the nvidia driver installer the error went away and the installer worked.

RECAP - installation of X-Plane: 

1.  Install the build-essential packages from the repos
```

sudo apt-get install build-essential
```

2.  Install the Nvidia drivers and say yes to install 32bit libs

3. make sure you have all 32bit libs as described in this thread [http://forums.x-plane.org/index.php?showtopic=34824](http://forums.x-plane.org/index.php?showtopic=34824).

4. Run the X-plane installer.

---

