---
title: "How to: install &amp; run Algodoo 1.7.1 on Ubuntu 32/64 bit"
date: 2010-06-26
forum: Gaming &amp; Leisure
---

### Post by adsbaer12 on 2010-06-26
Unfortunately a fresh installation Ubuntu 10.04 (32 bit or 64 bit) misses some dependencies. In order to install and run Algodoo 1.7.1 you should therefore proceed as follows:

_**step 1:**_ download the official .deb-file from the Algodoo website:
hXXp://XXX.algodoo.com/download/Algodoo_1_7_1-Linux32.deb
or
hXXp://XXX.algodoo.com/download/Algodoo_1_7_1-Linux64.deb
[replace "X"!]

_**step 2:**_ download and install the following dependencies before installing the actual .deb setup file:
- libcv1_1.0.0-6.2ubuntu1_amd64.deb
- libcvaux1_1.0.0-6.2ubuntu1_amd64.deb
- libhighgui1_1.0.0-6.2ubuntu1_amd64.deb
(you can search, find, and download them on hXXp://packages.ubuntu.com/)
[replace "X"!]

_**step 3:**_ after those three dependencies were successfully installed you now can proceed with the actual Algodoo setup by double-clicking on the .deb setup file Algodoo_1_7_1-Linux64.deb. (Note: You should *NOT* see a message that dependencies are missing)

_**step 4:**_ after setup completed successfully you can run Algodoo via terminal:
```
user@user-laptop:~$ /opt/Algodoo/algodoo
```(feel free to create a launcher)


In case you have a valid license for Algodoo 1.7.1. you may want to follow this additional _**step 5:**_
Algodoo's trial mode can not be unlocked when the program is started without administrative privileges! In order to be able to register Algodoo you have to run it at least ONCE as an administrator (note the SUDO prefix):
```
user@user-laptop:~$ sudo /opt/Algodoo/algodoo
```You may now enter your license information. Algodoo will acknowledge and store your registration data (that is of course only if it is actually valid).

From now on your Algodoo is registered/unlocked and can be run as a normal user without administrative privileges.

*Note: This tutorial may not apply to later versions of Algodoo and therefore renders obsolete.*

---

