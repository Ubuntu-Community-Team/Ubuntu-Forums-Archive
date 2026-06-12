---
title: "Can't find nvidia-xconfig"
date: 2006-06-03
forum: Desktop Environments
---

### Post by Twisted Mentat on 2006-06-03
I've just reinstalled ubuntu and I'm stuck at 1024x768 for my screen res.

I've followed the [BinaryDriverHowto/Nvidia](https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia#head-c737a8e39e49d924079ba3097055127ad3bb6cc8) in the wiki but I can't find the nvidia-xconfig package. I've enabled the restricted packages but still can't find them. The install is updated to the latest 5.10 and I also installed the kubuntu-desktop package as well as its dependencies. My video card is a NVIDIA 6800, AGP version.

Thanks in advance.

---

### Post by fornix on 2006-06-03
I have the same problem. I followed the same guide,
I have Nvidia Geforce MX2 grphics card. So as mentioned in the guide, installed nvidia-glx-legacy and i couldnt fine nvidia-xconfig. i just noticed a similar command nvidia-glx-config. so i typed the following command
```
nvidia-glx-config enable
```
Then i edited the /etc/X11/xorg.conf file so tht "nv" is replaced by "nvidia"
When i pressed Ctrl + Alt + Backspace, it gave fatal error. x couldnt start. i replaced "nvidia" to "nv" and got it working. Should i try the nvidia-glx driver? but as mentioned in tht wiki, as i use older card, i should use the legacy one. please help. Thanx in advance

---

