---
title: "cant change the resolution"
date: 2019-03-09
forum: Desktop Environments
---

### Post by samerkinaan on 2019-03-09
hello,
I am new to Linux and i having trouble changing the resolution on my screen, I have "RTX 2070" and "Dell S2417DG" monitor with (2560 x 1440) resolution and 144 refresh rate, and tried solutions on web but nothing worked, Ubuntu only gives me (1024 x 768) resolution.
any help would be appreciated.

---

### Post by CatKiller on 2019-03-09
> **samerkinaan said:**
> tried solutions on web but nothing worked
That provides exactly zero information. It's really not a helpful statement, except that it tells us that you may have already broken things in unspecified ways.

As a starting point, that graphics card came out after 18.04, which would be the sensible version of Ubuntu to be using, although you haven't said which version you are using. Support for Turing cards came with the 410 version of Nvidia's driver, so you'll need that version or higher. You can can get them from the graphics driver PPA.

---

### Post by samerkinaan on 2019-03-09
my OS version is Ubuntu 18.04.2 LTS, i think nvidia driver is causing the problem, when i write "lsmod | grep -i nvidia" command i get nothing, and when i try to open nvidia-settings i get this message:
 "ERROR: Unable to load info from any available system


(nvidia-settings:2565): GLib-GObject-CRITICAL **: 16:02:59.329: g_object_unref: assertion 'G_IS_OBJECT (object)' failed
** Message: 16:02:59.331: PRIME: No offloading required. Abort
** Message: 16:02:59.331: PRIME: is it supported? no"
and Nvidia X Server Settings is empty.
i tried installing the driver as in this link:[https://linuxconfig.org/how-to-install-the-nvidia-drivers-on-ubuntu-18-04-bionic-beaver-linux](https://linuxconfig.org/how-to-install-the-nvidia-drivers-on-ubuntu-18-04-bionic-beaver-linux)
and still didn't work

---

### Post by Autodave on 2019-03-09
The easiest way is to go to Additional Drivers in your settings and let it do the rest.

---

### Post by CatKiller on 2019-03-09
> **Autodave said:**
> The easiest way is to go to Additional Drivers in your settings and let it do the rest.

That is the easiest way, except that it doesn't yet include a version that supports Turing, AFAIK. For that, the OP needs to add the [graphics driver ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa). Once the ppa has been added, the newer driver versions will appear in the Additional Drivers tool. Provided they haven't done some mysterious thing prior to coming here.

---

