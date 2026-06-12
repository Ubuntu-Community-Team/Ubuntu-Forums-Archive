---
title: "Probs with one package and now apt is crashing every time"
date: 2006-08-27
forum: Desktop Environments
---

### Post by visvak on 2006-08-27
i was going thru the ubuntuguide on [www.ubuntuguide.org](www.ubuntuguide.org) and [installed this upslash theme]("http://ubuntuguide.org/wiki/Dapper#How_to_install_alternate_boot_splash_screen") called usplash-minimalistic. it dint install properly. gave some kinda wierd error saying linux-image 2.17.7 was not present.

and when i tried to uininstall it, it gave the same error again. then i downloaded the package from the web and tried to reisntall, again it returned the same error.

no i am unable to do anything related with apt as everytime it returns an error related to usplash-minimalistic.

does anyone know how to fix this ???? thanks in advance

---

### Post by tzulberti on 2006-08-27
Which is the error mesage that apears?

---

### Post by visvak on 2006-08-28
right now, im able to do stuff (as in install and unisntall) but everytime, after the operation is completed i get this error -

```

Setting up usplash-minimalistic (0.1) ...
Package `linux-image-2.6.17.7' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: linux-image-2.6.17.7 is not installed
dpkg: error processing usplash-minimalistic (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 usplash-minimalistic
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

and this happens even when i havent made any changes to the usplash-minimalistic package. it seems that everytime i do something in apt, it tries to reinstall or remove usplash-minimalistic.

---

### Post by DC@DR on 2006-08-28
Put this to the terminal:
```

sudo apt-get remove --purge your_broken_package
sudo apt-get autoclean

```
Hope this help with your problem :)

---

### Post by visvak on 2006-08-28
its fixed now thanks a lot guys. it had something to do with my kernel (i upgraded it to 2.17.7) all i had to do was boot into the old kernel and sudo apt-get remove and it was gone.

---

