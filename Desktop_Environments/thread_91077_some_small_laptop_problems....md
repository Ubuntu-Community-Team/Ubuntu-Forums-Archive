---
title: "some small laptop problems..."
date: 2005-11-16
forum: Desktop Environments
---

### Post by BenevolentParty on 2005-11-16
hey, i use ubuntu on a desktop and almost know what i am doing. i finally got around to installing it on my laptop (toshiba 1115-s103). i have run into a few problems...

first, i can't seem to figure out how to improve the screen resolution or the refresh rate. it is currently at 1024x768 with 60hz. i would like to at least get the refresh rate a bit higher...

also, my wireless card (mn-720) is living up to its maker (microsoft). i think i installed it right, i can get to it in system-admin-networking. it says its connected and configured right but i can seem to get online. 

thanks alot.

chris.

---

### Post by Ampersand on 2005-11-16
For the first problem
```
sudo dpkg-reconfigure xserver-xorg
``` should let you change the available resolutions.

For the wireless, run
```
iwconfig
```
and make sure the settings for your wireless card are correct. Mine has a tendancy to change itself to managed instead of ad-hoc mode occasionally, and it sometimes works if you put in the WEP key there (if you're using one).

---

