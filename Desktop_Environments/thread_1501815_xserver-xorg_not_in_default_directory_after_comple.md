---
title: "xserver-xorg not in default directory after complete removal and reinstall"
date: 2010-06-04
forum: Desktop Environments
---

### Post by Foeburner on 2010-06-04
I upgraded to Lucid Lynx when it first came out thinking it would fix my desktop (unable to set resolution higher than 800x600) and today I did a complete removal of xorg in synaptic package manager. 

Logged off and installed xorg again

```
sudo apt-get install xserver-xorg
```

everything installs fine in about 5mins (or at least long enough for me to take a wiz and come back) and start x

looks the same, 800x600 but when I opened the terminal, pressed up to reuse comman:

```
sudo gedit /etc/X11/xorg.conf
```

It brings up a blank file. I close it and asks me to save. Obviously new file. I navigate to the X11 folder and the conf file is not there. 

excuse my french but wtf?

I checked synaptics and all files are installed. 

By the way, video chipset is Volari Z7 XGI. Synaptics has the driver but does not work. I get monitor: unknown with default resolution. 

I have a Dell Poweredge SC430 server and I'm running ubuntu server and desktop.

All help is appreciated.  =D

---

### Post by Dusal on 2012-10-16
It's not problem. Since 8.04 Ubuntu don't using xorg.conf default. Although you can create it I think..

---

