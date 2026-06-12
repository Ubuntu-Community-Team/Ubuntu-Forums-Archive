---
title: "Gnome login screen vs. KDE login screen"
date: 2007-04-21
forum: Desktop Environments
---

### Post by playerTwo on 2007-04-21
I recently installed Kubuntu just to play around with it, and accidentally made it my default environment. The splash screen and the login screen are both now Kubuntu, but when I log in, it boots Ubuntu normally. Is there a way I can change the splash and login screen back to the Ubuntu theme?

---

### Post by Ateo on 2007-04-28
If you are like me and you don't mount /boot at system startup, mount it (if you have no idea what I am talking about, you can safely skip this step):```
$ sudo mount /boot
```

Do:```
sudo update-alternatives --config usplash-artwork.so
```

Choose which one you want and finally:```
sudo dpkg-reconfigure linux-image-`uname -r`
```

If you are dual booting, make sure you verify that menu.1st has all your available OSs. For some reason, reconfiguring mine removes the windows entry from one of my installations.... so, just FYI.

I do believe you can remove the 'usplash artwork' for both KDE and XCFE if you want. Neither depends on their respective meta-package.

---

### Post by aysiu on 2007-04-28
And don't forget...

Press Control-Alt-F1

Log in

Type ```
sudo /etc/init.d/kdm stop
sudo nano /etc/X11/default-display-manager
``` Change ```
/usr/bin/kdm
``` to ```
/usr/sbin/gdm
``` Save (Control-X, Y, Enter) ```
sudo /etc/init.d/gdm restart
```

---

### Post by elyk on 2007-05-02
An easier method (which I have used before) is to simply open a terminal, and type ```
sudo dpkg-reconfigure gdm
```; after you hit ok to get past the screen explaining display managers you should be given a choice of gdm or kdm; choose gdm, reboot, and you should be back where you were originally.

---

### Post by Sushubh on 2007-05-15
yey fixed. :D

---

