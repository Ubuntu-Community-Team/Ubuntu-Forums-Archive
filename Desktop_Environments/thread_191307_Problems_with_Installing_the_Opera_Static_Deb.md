---
title: "Problems with Installing the Opera Static Deb"
date: 2006-06-07
forum: Desktop Environments
---

### Post by kkathman on 2006-06-07
Apparently, Opera doesnt have a Dapper version at present, and I was told to install the static Opera deb from that site. I downloaded, and attempted to install with dpkg but got a dependency error stating that it needed xlib6g >3.3.6 and xlibs.  

I searched the apt-cache and found xlibs-dev and libx11-dev and installed them both. However I still get the same error.

Im obviously not installing the correct dev but dont seem to find another based on descriptions at least. Could someone help me on getting Opera set up in Dapper?

I was told that Opera-Breezy would not work, btw.

Thanks
kkathman

---

### Post by Case_f on 2006-06-07
I'd suggest installing Opera 9 beta 2, it's very stable and usable, it should have resolved these issues and you can use the shared version, you're not forced to use static anymore. 

Otherwise, this thread might help you:

[http://ubuntuforums.org/showthread.php?t=124968](http://ubuntuforums.org/showthread.php?t=124968)

---

### Post by CronoDekar on 2006-06-07
According to the [wiki article](https://wiki.ubuntu.com/OperaBrowser), you just need to install the deb here:

[http://archive.ubuntu.com/ubuntu/pool/main/x/xorg/xlibs_6.8.2-77_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/x/xorg/xlibs_6.8.2-77_all.deb)

---

