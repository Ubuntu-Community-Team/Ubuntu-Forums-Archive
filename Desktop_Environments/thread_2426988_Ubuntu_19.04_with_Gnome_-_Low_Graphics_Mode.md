---
title: "Ubuntu 19.04 with Gnome - Low Graphics Mode?"
date: 2019-09-16
forum: Desktop Environments
---

### Post by Farenheit on 2019-09-16
Is there a low graphics mode in Ubuntu 19.04?  It looks like this existed in previous versions of Ubuntu with Unity, but I can't find anything that enables it in Gnome.  I've installed 19.04 on a Fitlet Micro PC with a Radeon R6 in it.  Graphics work as is, but is a bit slow.  Thanks!

---

### Post by mörgæs on 2019-09-16
If you want a Buntu which is lighter in graphics then X/Lubuntu are worth a try.

---

### Post by Farenheit on 2019-09-16
Thanks.  So that means there's no option to reduce graphics in 19.04 with Gnome?

---

### Post by cruzer001 on 2019-09-16
I do not run 19.04 so I cannot say whats available.

If you want to stick with the Gnome you may want to try the lighter Ubuntu Budgie.  It works for me on an old laptop that cannot run Ubuntu Gnome.

---

### Post by Farenheit on 2019-09-18
I ended up loading [XFCE4 Desktop Environment]("https://xfce.org/") (which Xubuntu uses) on my 19.04 install.  This gives a basic desktop without the heavy graphical requirements that Ubuntu Gnome has.  However, it keeps Ubuntu Gnome intact, so you can choose between them.  I'll put down the steps I followed for others that may be interested:

```
sudo apt install xfce4 libexo-1-0
sudo shutdown -r now
```

It took me forever to figure out how to choose the desktop environment, because in 19.04, the button isn't as intuitive as it used to be :oops:.  But on the login screen, to the right of your login name, you can click the button to bring up the choice of desktop environments.  I chose "Xfce Session" and it remembers it after reboots.  There are some functionality trade-offs, but it navigates much faster on my micro PC.

[ATTACH=CONFIG]284034[/ATTACH]

---

