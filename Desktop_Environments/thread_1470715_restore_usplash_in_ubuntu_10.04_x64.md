---
title: "restore usplash in ubuntu 10.04 x64"
date: 2010-05-03
forum: Desktop Environments
---

### Post by Firidan on 2010-05-03
Sometime ago I installed Kubuntu-desktop. I didn't like it and uninstalled it later on. But the splash screen didn't change back to Ubuntu's default. It shows a DISTORTED and TWISTED image of the Kubuntu splash screen during boot. I tried the following command:

sudo update-alternatives --config usplash-artwork.so

result:

update-alternatives: error: no alternatives for usplash-artwork.so

So checked in the Synaptic. It turns out none of the splash packages and usplash package itself are installed:confused:. So I tried to install usplash. Then I got error message that says that I will have to remove certain packages in order to install usplash. The problem is that "certain packages" are ALL installed packages including gnome, most of kernel modules, all programs and the X server. So obviously I pressed cancel.

Then I tried to install via the terminal:

sudo apt-get install usplash

output:

Somepackages could not be installed.
The following packages have dependencies that can't be satisfied:
usplash: 
dependency: initramfs-tools (>= 0.92bubuntu55) but it will not be installed
depedency: upstart (>= 0.6.3-4) but it will not be installed
Recommended: usplash-theme-ubuntu but it will not be installed
E: Broken packages.

I checked in Synaptic I have initramfs-tools(0.92bubuntu78) and upstart0.6.5-6. I reinstalled them but it didn't help.

Help please!:confused:

---

### Post by 3rdalbum on 2010-05-03
Whoa, no, Ubuntu 10.04 doesn't use Usplash or Xsplash. It uses Plymouth.

Try removing "plymouth-theme-kubuntu-logo" and reinstalling "plymouth-theme-ubuntu-logo". I'm sure you could just use update-alternatives to accomplish the same task, but I don't know how to do it.

---

### Post by Firidan on 2010-05-03
Thanks. It works:P

---

### Post by Terry Zhou on 2010-05-03
> **3rdalbum said:**
> Whoa, no, Ubuntu 10.04 doesn't use Usplash or Xsplash. It uses Plymouth.

Try removing "plymouth-theme-kubuntu-logo" and reinstalling "plymouth-theme-ubuntu-logo". I'm sure you could just use update-alternatives to accomplish the same task, but I don't know how to do it.

Thanks, dude, you save my day!:D

---

### Post by lucaspr on 2010-06-05
Thanks! I removed the wrong splash screens too.

Now I got rid of the kubuntu theme!

---

