---
title: "XGL install problem : start&amp;crash"
date: 2006-06-02
forum: Desktop Environments
---

### Post by mfyz on 2006-06-02
i want to install XGL, xcomposite works good..

i installed xserver-xgli compiz gnome-compiz & depended packages which in howtos
when i change my gdm.conf file to 0=Xgl and try to start gdm service, i see cursor and then X crashes, 1 or 2 sec. wait & again starts, again crashes.. loops this..

what's the problem? i cant start my X with xgl driver..

---

### Post by 23meg on 2006-06-02
Please state which guide you followed, what video hardware you have, and post copies of your xorg.conf and gdm-custom.conf .

---

### Post by mfyz on 2006-06-02
my video card is intel 85x i'm using my GL extensions in my desktop games, xcomposite..

i try to catch errors, in my xorg.log file there is no errors. bunt gdm.log contains 1 error.. 

dlopen: /usr/lib/xorg/modules/extensions/libGLcore.so: undefined symbol: __glXLastContext
(EE) Failed to load /usr/lib/xorg/modules/extensions/libGLcore.so
(EE) Failed to load module "GLcore" (loader failed, 7)


i followed too many guides.. i try to do it with all howtos, forum threads in ubuntuforums.. no success..

---

### Post by mfyz on 2006-06-02
my xorg.conf & gdm.conf..

---

