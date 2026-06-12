---
title: "Compiz Fusion and Nvidia Help"
date: 2007-09-15
forum: Desktop Effects &amp; Customization
---

### Post by d0ugb on 2007-09-15
I have been trying for days to get Compiz-Fusion working, i have tried many different howto's and havent had any luck getting it working. I have followed the howto on this site:  [http://kevin.vanzonneveld.net/techblog/article/enable_compizfusion_in_ubuntu_feisty/](http://kevin.vanzonneveld.net/techblog/article/enable_compizfusion_in_ubuntu_feisty/). I have full 3d accel working with the nvidia drivers but everytime i run compiz --replace i get this error```
d0ugb@d0ugb-desktop:~$ compiz --replace/usr/bin/compiz: line 777:  8324 Segmentation fault      (core dumped) $*

```
 
Anyone have any clue what might be causing it?

---

### Post by praet on 2007-09-17
I recommend removing the existing compiz and reinstall using amaranths repo (recommended) as described here:
[https://help.ubuntu.com/community/CompositeManager/CompizFusion](https://help.ubuntu.com/community/CompositeManager/CompizFusion)

Basically:
```
sudo apt-get --purge remove compiz* libcompizconfig*
```

Then remove trevino's repo and add Amaranths in /etc/apt/sources.list
```
deb http://ppa.launchpad.net/amaranth/ubuntu feisty main
deb-src http://ppa.launchpad.net/amaranth/ubuntu feisty main
```

Then reinstall compiz:
```
sudo apt-get update && sudo apt-get dist-upgrade && sudo apt-get install compiz compizconfig-settings-manager 
```

---

