---
title: "Cleaner lighter Desktop"
date: 2009-07-13
forum: Desktop Environments
---

### Post by bhavin66 on 2009-07-13
I have been a ubuntu user for past few years for the most part i like it.
Lately i have been trying to get the system leaner and cleaner.
First thing was to get rid of evolution, pidgin and stuff like that.
After little digging i was able to remove evolution but when i run the update everything just comes back with "ubuntu-Desktop"
Just trying to find a way to have a lean clean desktop with options to install what i need.

---

### Post by lykwydchykyn on 2009-07-13
"ubuntu-desktop" is a meta package, meaning it contains nothing but depends on all the various packages that come with the default Ubuntu desktop.  So if you want to start taking things like evolution and pidgin away, the first thing to do is remove ubuntu-desktop.  It should have been removed anyway when you removed evolution, IIRC.

There are a lot of ways to achieve "lean and clean" if that's what you're looking for.  You might even look into running a minimal window manager like openbox or fluxbox instead of GNOME.

---

### Post by Ra-Hoor-Khuit on 2009-07-13
Reinstall using the Minimal Install CD, maybe?

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

I would think that would give you the control you want over what gets installed.

---

### Post by bhavin66 on 2009-07-13
I like to use GNOME. It's just that i use web browser, VLC and openoffice most of the time and SSH, terminal and vmware sometimes.
Agreed i can use other WM but as everybody in the house is used to this WM i would like to stick to it and have it leaner.

---

### Post by kerry_s on 2009-07-13
yeah, install the base(cli) then build it up from there.

**sudo apt-get install xorg gdm gnome-core**

---

