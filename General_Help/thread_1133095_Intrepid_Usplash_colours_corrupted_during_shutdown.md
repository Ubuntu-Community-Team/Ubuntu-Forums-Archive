---
title: "Intrepid Usplash colours corrupted during shutdown"
date: 2009-04-22
forum: General Help
---

### Post by aniruddha on 2009-04-22
Hello all. I have posted this before in a couple of threads but haven't gotten any responses. Apologies if this has been dealt with, but I cannot, for the life of me, seem to find a fix. 

Essentially, I am unable to get a full screen Usplash on my 1280x800 monitor. This would not be such a major issue, however I am also experiencing some sort of graphical corruption during shutdown. The colours are corrupted so it looks as if someone has thrown neon paint onto my precious usplash theme. Sighs. 

I am using a Lenovo Y530, with a Nvidia 9500M G (the latest 180 drivers for Intrepid) on Intrepid 64bit. Compiz is enabled. I had recompiled the "ubuntu-sunrise" theme from gnome-look, chnaged my menu.lst file to the vga value using hwinfo to match the 1280x800, 8-bit (0x0361) value and edited usplash.conf to x=1280 and y=800. My startupmanager is configured to 640x480, 8 bits. If no fix is possible, does anyone know if this problem persits in Jaunty?

Any help would be appreciated. Thanks guys.

---

### Post by Yashiro on 2009-04-22
Try nvidia 180.51 and revert the changes you've made to see if it stops the error.

It usually occurs when the palette change is unsupported or doesn't work. Even if your card says it supports certain modes, occasionally it just fails in this manner.

---

### Post by altonbr on 2009-04-22
This happened to me using nVidia drivers in Intrepid. I've upgrade to Jaunty and no longer have any problems :)

---

### Post by cubeist on 2009-04-22
Could be a driver issue as mentioned above, but sometimes you just need a quick re-configure of usplash...

```
sudo dpkg-reconfigure usplash
```

---

### Post by aniruddha on 2009-04-22
Thanks for the tips guys. +1 to upgrade.

---

