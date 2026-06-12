---
title: "&quot;Restricted driver manager&quot; on Debian"
date: 2007-12-04
forum: Debian
---

### Post by Fixman on 2007-12-04
OK, I know this is probably impossible, but I have an nVidia video card that uses a propietary driver, and so in Ubuntu I made it work with the restricted drivers manager. Is there any way to do so in Debian?

---

### Post by Antman on 2007-12-04
> **Fixman said:**
> OK, I know this is probably impossible, but I have an nVidia video card that uses a propietary driver, and so in Ubuntu I made it work with the restricted drivers manager. Is there any way to do so in Debian?

Try Envy [http://albertomilone.com/nvidia_scripts1.html]("http://albertomilone.com/nvidia_scripts1.html")

or 

Automatix [http://www.getautomatix.com/forum/index.php?showtopic=1652]("http://www.getautomatix.com/forum/index.php?showtopic=1652")

---

### Post by deanjm1963 on 2007-12-20
if you're using etch it's very simple to install nvidia drivers, either the debian way or the "manual" way.

the debian way is this. in a terminal as root user

apt-get install build-essential module-assistant linux-headers-2.6-686 (change to appropriate kernel)

m-a prepare
auto-install nvidia
apt-get install nvidia-glx nvidia-settings
modprobe nvidia

and restart

the manual way

first download the lastest nvidia driver and put it somewhere, I keep it in opt

in a terminal as root user

apt-get install build-essential linux-headers-2.6-686 (change to appropriate kernel)

log out and hit Ctrl+Alt+F1 which will give you a full screen terminal

log in as root if you have enabled root user access or your account and su

then type the following

/etc/init.d/gdm stop
sh /path to where nvidia driver is/NV (and hit tab, no need to type NVIDIA-etc, the tab key will fill it in for you) and hit enter
follow the instructions, say YES to everything as it prompts you

once finished installing, type

/etc/init.d/gdm start

that will take you back to the GDM

I suggest a restart

hope this helps

---

