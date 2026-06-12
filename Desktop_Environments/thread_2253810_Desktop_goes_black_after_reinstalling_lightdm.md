---
title: "Desktop goes black after reinstalling lightdm"
date: 2014-11-22
forum: Desktop Environments
---

### Post by Krzysztof_Witkowsk on 2014-11-22
Hi,
I recently wanted to try some other DM, like Gnome DM or KDM. After installing Gnome DM, the part of the screen on which are icons went black and I couldn't add any icons there. Everything else worked fine, except there was an app switcher from Unity DM and "status bar" from Gnome. I tried uninstalling gdm package and everything else that gdm depends on, but nothing happened. Same thing with KDM. Then I tried ```
sudo apt-get install --reinstall lightdm ubuntu-desktop
``` but it accidentally installed EVERY possible DM available and set that one from Lubuntu. I tried edditing /etc/X11/default-display-manager, but there was lightdm, so I haven't changed anything. Can I uninstall all these DMs and go back to the default lightdm?

PS. Sorry for my language

---

### Post by ibjsb4 on 2014-11-23
First be sure which one you are on.
```
cat /etc/X11/default-display-manager
```
If it comes up lightdm.
```
sudo dpkg-reconfigure lightdm
```
[http://www.webupd8.org/2011/07/how-to-switch-between-gdm-lightdm-or.html](http://www.webupd8.org/2011/07/how-to-switch-between-gdm-lightdm-or.html)

---

### Post by Krzysztof_Witkowsk on 2014-11-23
Nothing happened. I think that some of the DMs that I installed modified lightdm.

EDIT: I can't go into tty* by pressing Ctrl-Alt-F* (noting happens) and I tried installing gdm and setting it as default. On the loading screen still there is "Lubuntu 14.10", login screen is from gdm and everything else is from Lubuntu.

---

### Post by ibjsb4 on 2014-11-23
Do you get to the login screen?  If so, Ctrl-Alt-F1 will not work?  

What about at the grub boot, can you enter recovery mode?

---

### Post by Krzysztof_Witkowsk on 2014-11-24
I decided to reinstall ubuntu and it helped. I think that the problem was that I installed only kdm, not kubuntu-desktop.

---

### Post by ibjsb4 on 2014-11-24
Installing kubuntu-desktop will pull in a lot of packages.  

[http://packages.ubuntu.com/trusty/kubuntu-desktop](http://packages.ubuntu.com/trusty/kubuntu-desktop)

If you wish to add it to your current install, leave off the recommended packages.
```
sudo apt-get install --no-install-recommends kubuntu-desktop
```

---

