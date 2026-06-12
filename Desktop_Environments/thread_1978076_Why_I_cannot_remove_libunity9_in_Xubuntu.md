---
title: "Why I cannot remove libunity9 in Xubuntu?"
date: 2012-05-11
forum: Desktop Environments
---

### Post by kholis on 2012-05-11
Since I don't use unity, why I cannot remove libunity9 package in Xubuntu?

Remove this package will also remove many software such as: brasero, shotwell and usb-creator-gtk

```

$ sudo apt-get remove libunity9
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libraw5 brasero-common libunique-3.0-0 libgexiv2-1 dvd+rw-tools librest-0.7-0 libtotem-plparser17 libquvi-scripts
  libgmime-2.6-0 growisofs libquvi7
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  brasero brasero-cdrkit gir1.2-unity-5.0 libbrasero-media3-1 libunity9 shotwell usb-creator-gtk
0 upgraded, 0 newly installed, 7 to remove and 0 not upgraded.
After this operation, 11.4 MB disk space will be freed.
Do you want to continue [Y/n]? 

```

---

### Post by mc4man on 2012-05-11
If you wish to waste any more time on this then various opinions, ect. concerning the build dep on libunity for  other packages
[http://ubuntuforums.org/showthread.php?t=1814257&highlight=libunity+remove](http://ubuntuforums.org/showthread.php?t=1814257&highlight=libunity+remove)

---

### Post by kholis on 2012-05-11
> **mc4man said:**
> If you wish to waste any more time on this then various opinions, ect. concerning the build dep on libunity for  other packages
[http://ubuntuforums.org/showthread.php?t=1814257&highlight=libunity+remove](http://ubuntuforums.org/showthread.php?t=1814257&highlight=libunity+remove)
Oh my... I just realized that canonical try to force us to use unity. This is terrible.

I choose to remove libunity and will compile those software from upstream.

Thanks

---

