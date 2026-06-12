---
title: "XGL &amp; Beryl 3D Accel. problems on Geforce 5200"
date: 2006-11-11
forum: Desktop Environments
---

### Post by alusic on 2006-11-11
Hi there,

I have installed Ubuntu 6.10 Edgy Eft on my computer, which has a Geforce FX5200 (128MB), and installed and configured nvidia-glx drivers properly. 3D Acceleration was working according to "glxinfo | grep direct".

After installing XGL and Beryl, the command above reports that there's no 3D Acceleration. What's wrong?

In order to install and configure and install XGL, Beryl and nVidia drivers I used the following links:

[Link 1]("https://help.ubuntu.com/community/CompositeManager/Xgl?highlight=%28xgl%29")
[Link 2]("https://help.ubuntu.com/community/BerylOnEdgy?highlight=%28beryl%29")

Since 3D Acceleration stopped working I followed Link 2's tutorial in order to replace the nVidia driver but 3D Acceleration still doesn't work.

I've also edited the xorg.conf file according to the links above.

Regards,

---

### Post by patrickfromspain on 2006-11-11
you don't need XGL anymore with edgy. Just install beryl and the newest nvidia drivers from [www.nvidia.com](www.nvidia.com) and you're ready to go ;)

---

### Post by alusic on 2006-11-11
> **patrickfromspain said:**
> you don't need XGL anymore with edgy. Just install beryl and the newest nvidia drivers from [www.nvidia.com](www.nvidia.com) and you're ready to go ;)

](*,) 
Thanks a lot!!!! Now everything is working and superfast!!!

Do you know if XGL and/or Beryl work on Solaris 10?

Regards,

---

