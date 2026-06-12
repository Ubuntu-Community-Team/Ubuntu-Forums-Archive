---
title: "nVIDIA Drivers on 8.04, Low Graphics on reboot"
date: 2009-01-06
forum: General Help
---

### Post by -Saint on 2009-01-06
Well before anyone replies, the following don't work:
- EnvyNG
- System > Administration > Hardware Drivers

I currently own a GTX 260 and the 177.82 are the only drivers that work with it.

My problem is that I stop X, I install the drivers (they ask me to compile kernel, and they will do it for me), but they install successfully and I am able to get desktop 3D and full resolution. Now, after I reboot they go back into "Low-Graphics" mode and it cannot detect my video card.

Help?

---

### Post by gettinoriginal on 2009-01-06
In terminal, try this:

```
 startx 
```

then if that fails, try

```
 sudo dpkg --configure xserver-xorg 
```

---

### Post by -Saint on 2009-01-06
That doesn't do anything sadly and I am starting to get pissed off at Ubuntu.

---

