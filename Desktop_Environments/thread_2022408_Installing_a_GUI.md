---
title: "Installing a GUI"
date: 2012-07-10
forum: Desktop Environments
---

### Post by Teslafan on 2012-07-10
Hi there.

I've been trying to produce my own linux thing. Therefore i used minimalCD, installed it with the bare minimum and, from there, started to build the "distro" if you allow me to say so.

Now, I got to a point where i want to add a GUI to it, and that that GUI gets initiated automatically, but i can't seem to get it working.

I thought I only needed to sudo apt-get install "chosen gui", reboot and that's it. Wrong.

I tried Enlightenment and Fluxbox and i could only go to the GUI after a startx in the command prompt.

What am i missing? (ubuntu desktop is a no go since it's too big and i'm doing this to install in a 6+ years old computer).

Thanks for your input.

---

### Post by wojox on 2012-07-10
A diplay manager is needed if you don't want to startx manually. [URL="http://www.freedesktop.org/wiki/Software/LightDM"]The Light Display Manager (LightDM)

[/URL]

---

### Post by Marco0551 on 2012-07-10
You need something like GDM or one of the other Display Managers see: [URL="http://en.wikipedia.org/wiki/X_display_manager_%28program_type%29#Some_implementations"]http://en.wikipedia.org/wiki/X_display_manager_%28program_type%29#Some_implementations
[/URL]

---

### Post by Teslafan on 2012-07-10
Thanks fellas.

Will try it first thing in the morning. :popcorn:

---

### Post by zwygart on 2012-07-10
There are several ways to start a window manager : if you want a fancy one, look at tutoriels of distro wich are build by hand like archlinux and gentoo. 

One of the easiest way is to install a "login manager" like GDM (gnome) or KDM (kde). 

Another way is to just add a line in your .bashrc file. Append the "startx" command at the end of the file. (or "startx &" at beginning). But this method has several disadventages. First this file is executed each time you start a terminal (tty or gnome-terminal, etc.). So if your GUI is already started, this will generate a error but nothing more. If you don't use the terminal a lot, this will not be significant. Another disadventage is it will be harder to mount USB keys or similar filesystems. 

So the best will be just install gdm or kdm or any other taste and you'll be fine.

---

### Post by lolpenguin on 2012-07-11
Since in Arch you start with a minimal install, the Arch Wiki is useful for setting up stuff such as X and a desktop environment.

---

### Post by zwygart on 2012-07-11
[https://wiki.archlinux.org/index.php/Display_manager](https://wiki.archlinux.org/index.php/Display_manager)

---

