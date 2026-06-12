---
title: "Ubuntu FAILS TO LOAD, NEED HELP ASAP--CLASS IN AN HOUR"
date: 2007-08-28
forum: Desktop Environments
---

### Post by brokenbuntu on 2007-08-28
I recently used "sudo apt-get install nvidia-glx-new" to install drivers for my NVidia Go 7400. I had also installed drivers from this tutorial: [http://kevin.vanzonneveld.net/techblog/article/enable_compizfusion_in_ubuntu_feisty/](http://kevin.vanzonneveld.net/techblog/article/enable_compizfusion_in_ubuntu_feisty/)

When I start my computer, ubuntu fails to load the desktop correctly. This is extremely problematic because I use that same laptop to take notes, and have class in an hour! (I'm currently using a friend's laptop).

This is the error in question:

**Failed to start X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?**

When I click "yes" it essentially states my specs and says "Log file: "/var/log/Xorg.0.log"", as well as "Using config file: "/etc/X11/xorg.conf"".

If I can't solve this in an hour, I at least need to know how to take notes with the command line, which I can access through alt+ctrl+backspace.

I am extremely grateful for any help.

---

### Post by K.Mandla on 2007-08-28
Edit your /etc/X11/xorg.conf file to use the nv or vesa driver instead, and try restarting X.

```
sudo nano -w /etc/X11/xorg.conf
```
Change 

```
Driver "nvidia"
```
to

```
Driver "nv"
```
Use "vesa" if "nv" still doesn't work.

Later on, after class, you can figure out what went wrong. Good luck! [-o<

---

### Post by brokenbuntu on 2007-08-28
When use the command "sudo nano -w /etc/X11/xorg.conf/" there is a large black space with no text, with some commands on the bottom (^G, ^O etc) that don't seem to do anything and a title bar at the top ("GNU nano 2.0.2"). Is this supposed to be this way, and if so, how do I change the driver to what you specified?

EDIT: Didn't know that ^ meant CTRL, but I do now after a wild guess. Will get back to you asap!

---

### Post by brokenbuntu on 2007-08-28
IT WORKED!

K-Mandla, you're amazing. :guitar:

---

### Post by K.Mandla on 2007-08-28
There shouldn't be a slash after the xorg.conf, so it might be editing an empty file. If it comes up empty even after that, then you're missing the file, which is why the desktop wouldn't start. :roll:

When you're done editing, press CTRL+O to save the file, and CTRL+X to exit. Then 

```
startx
```
and you *should* be back on track. ;)

Edit: Ah, cool. It worked. Good luck in class. ;)

---

### Post by yellowband on 2007-08-28
when you are ready to retry instlalling your video driver, look for a script called "envy". do a google search for "envy script ubuntu"

its great. very easy to install, adn it it installs the latest driver for your video card. it also automatically writes your xorg.conf file so that xserver error shouldn't happen again.

---

