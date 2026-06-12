---
title: "[UBUNTU 18.04] Change scale-factor from command line is not working"
date: 2018-05-14
forum: Desktop Environments
---

### Post by fercal on 2018-05-14
Dear all,

I am trying to change the scale-factor from the command line. I have tried the following command, but it is not working:

gsettings set org.gnome.desktop.interface scaling-factor 2

Actually, I can modify the scaling factor using the GUI of the GNOME control Center, but the value in org.gnome.desktop.interface scaling-factor remains to 0. So, I guess that the value of scaling-factor is ignored and the GNOME control center uses a different mechanism to set the scaling-factor. Does anyone know how to change the scale factor from the command line?

Thanks in advance,
Fernando

---

### Post by viljami on 2018-07-09
I have the same problem. I'm using 18.04 too. I can use xrandr to set resolution and some crude scaling but it is not rendering the extra pixels it just scales up and thus looks bad. I'd like to make desktop icons that set the resolution to 1080p at 1x scaling an another one that sets it to 4K at 2x scaling.

---

