---
title: "fvwm-crystal"
date: 2006-02-15
forum: Desktop Environments
---

### Post by joplass on 2006-02-15
Has anyone intalled this program?  Or does anyone know how to install it?  I am looking for steps.
 Thanks

---

### Post by ekerazha on 2006-04-21
There isn't any fvwm-crystal package :( 

You could try to follow these steps: [http://fvwm-crystal.org/download.html](http://fvwm-crystal.org/download.html)

> 
You can find stable releases of FVWM-Crystal in the download area. Requirements are described at the bottom of this page. Installation is pretty strightforward - unpack the package to a separate directory and run command:

make install

FVWM-Crystal will be installed in /usr/local directory by default (you need to have root privileges). If you want to change the default installation directory, you can do this by running command:

make PREFIX=/usr install

If you don't have your own ~/.Xresources, you can grab one from addons/ directory included in the package. Without it terminal windows will be unconfigured. If you use login manager, such as gdm or kdm, copy file addons/fvwm-crystal.desktop to /usr/share/xsessions - now you will be able to select "FVWM-Crystal" from the "Sessions" menu. If you prefer startx, you can grab example ~/.Xsession (or ~/.xinitrc) file from addons/ directory.

Now everything should be set up. You can now restart your X session and enjoy your new desktop :)


---

### Post by K.Mandla on 2007-01-21
In case anyone else ever wonders. ...

[https://help.ubuntu.com/community/FVWM-Crystal](https://help.ubuntu.com/community/FVWM-Crystal)

---

