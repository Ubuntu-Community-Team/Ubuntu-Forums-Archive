---
title: "Ubuntu starts, but the screen is blank!"
date: 2011-10-22
forum: Desktop Environments
---

### Post by nokiau on 2011-10-22
Hello! I have a litle problem. I upgraded Ubuntu to latest version(11.10) and I didn't like gnome 3, so I tried to downgrade gnome 3 to gnome 2 using dggnome3 ([https://launchpad.net/~lkjoel/+archive/dggnome3](https://launchpad.net/~lkjoel/+archive/dggnome3) ). After reboot I loged in on the new interface, but it was a bad interface. In addiction, that pack modifyed gnome 3 too. I tried to fully uninstall gnome by running in terminal sudo apt-get remove gnome-*. Now, after reboot, ubuntu boots, but my screen is blank. I can't access terminal. I can use only recovery console. What should I do to fix it?

---

### Post by Frogs Hair on 2011-10-22
Hello and Welcome

The PPA you used was for removing a Gnome 3 PPA , which is different than the completed version.

If you are using 11.10 you can't restore Gnome 2 because it never had it to begin with . The PPA you used was for people trying Gnome 3 on a Gnome 2 based distribution . You could have just chose to boot Ubuntu and removed Gnome 3 shell from the software center or synaptic if it was installed from there .

I would start over if I were you , without terminal access you won't be able to install any desktop environment . PPAS are use at your own risk , so make sure you understand what they do before using them .

---

### Post by nokiau on 2011-10-22
I have a lot of important things in my home folder and i can't access it because it is encrypted. Other solution?

---

### Post by Frogs Hair on 2011-10-22
You may be able access Ubuntu or attempt some kind of repair from a Live cd if you have one .

---

