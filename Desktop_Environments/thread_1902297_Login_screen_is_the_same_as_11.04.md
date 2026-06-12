---
title: "Login screen is the same as 11.04"
date: 2011-12-30
forum: Desktop Environments
---

### Post by Bajinga on 2011-12-30
Recently, I downloaded the KDE environment, just to see how it was, and after a few days, I decided that it wasn't as good as Unity.

So, I removed the download from the Download Centre, rid of the main packages from the synaptic manager (which, in turn, broke the KDE packages that could only run with the mains), then removed all of the broken files.

However, I am still left with a few... Hitches:

1.) The GRUB screen is still a blue colour, as opposed to the purple. (I like the blue much more, really, so I cannot complain)

2.) The load-up screen still reads, "KUBUNTU". (Again, I don't really care)

3.) The login screen is that of 11.04, and I am running 11.10. What is even more strange, is that, even with something like Simple LightDM Manager, I can't do the simplest thing, say: change the background.

Here is the login screen:

[[IMG]http://img576.imageshack.us/img576/3889/dscn0061m.th.jpg[/IMG]](http://imageshack.us/photo/my-images/576/dscn0061m.jpg/)

---

### Post by lolpenguin on 2012-01-07
I can't tell if it's LightDM without unity-greeter or GDM, so I can't help.
But I can with the boot splash. Uninstall kubuntu-plymouth-theme (or something similar) and reinstall the one with ubuntu in it's name.

---

### Post by llelectronics on 2012-01-08
From the screenshot I guess its gdm3 running there. 
Try switching to lightdm (if it is still installed) by executing 
```
sudo dpkg-reconfigure lightdm
```
in a terminal. It will ask you which display manager to use. Just choose lightdm here and press enter. Then restart. It now should show you the lightdm display manager which is used by default on Ubuntu 11.10

---

