---
title: "changing the splash screen"
date: 2009-05-30
forum: General Help
---

### Post by Mattyk on 2009-05-30
Is it possible to change the ubuntu splash screen that you get before login? If so how?

---

### Post by Legace on 2009-05-30
Simply install StartUp-Manager (via Synaptic) and select **yourtheme.so** as your uSpalsh theme in StartUp Manager.

If You doesn't work:

- Install some build utilities
1.) sudo apt-get install cdbs debhelper dpkg-dev fakeroot devscripts autotools-dev
2.) sudo apt-get install libusplash-dev
- Install the build dependencies for the usplash stuff
3.) sudo apt-get build-dep usplash-theme-ubuntu

- Get the source code - I'd base it on the crunchybranch_usplash.
4.) Copy file crunchybranch_usplash.so to /usr/lib/usplash.
5.) sudo update-alternatives --install /usr/lib/usplash/usplash-artwork.so usplash-artwork.so /usr/lib/usplash/crunchybranch_usplash.so 10
6.) sudo update-alternatives --config usplash-artwork.so && sudo update-initramfs -u

- If You choose another resolution, You must edit file:
7.) sudo gedit /etc/usplash.conf
# Usplash configuration file
xres= "your X-resolution"
yres= "your Y-resolution"

- Test it witch:
8.)sudo usplash -c

---

### Post by randolf_ambrose on 2010-12-19
> **Legace said:**
> Simply install StartUp-Manager (via Synaptic) and select **yourtheme.so** as your uSpalsh theme in StartUp Manager.

If You doesn't work:

- Install some build utilities
1.) sudo apt-get install cdbs debhelper dpkg-dev fakeroot devscripts autotools-dev
2.) sudo apt-get install libusplash-dev
- Install the build dependencies for the usplash stuff
3.) sudo apt-get build-dep usplash-theme-ubuntu

- Get the source code - I'd base it on the crunchybranch_usplash.
4.) Copy file crunchybranch_usplash.so to /usr/lib/usplash.
5.) sudo update-alternatives --install /usr/lib/usplash/usplash-artwork.so usplash-artwork.so /usr/lib/usplash/crunchybranch_usplash.so 10
6.) sudo update-alternatives --config usplash-artwork.so && sudo update-initramfs -u

- If You choose another resolution, You must edit file:
7.) sudo gedit /etc/usplash.conf
# Usplash configuration file
xres= "your X-resolution"
yres= "your Y-resolution"

- Test it witch:
8.)sudo usplash -c

i have installed the startup-manager in lucid... there is no option to browse/select and install themes or any such...

so i tried the second option... crunchybranch_usplash.so is not available for download...

what are the alternatives or do you have the required files???

---

