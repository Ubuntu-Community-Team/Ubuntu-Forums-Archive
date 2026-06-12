---
title: "Ubuntu has symlinked /bin/sh to /bin/dash"
date: 2009-05-18
forum: General Help
---

### Post by junglejuice on 2009-05-18
hi there
i'm trying to install the package thinliquidfilm for converting video to mp4 with h.264. but the package will not install because Ubuntu has symlinked /bin/sh to /bin/dash. i understand that running this code ```
sudo rm -f /bin/sh
sudo ln -s /bin/bash /bin/sh
```
will fix this problem but will it break any existing packages i've installed or will it be a problem for the future when i try to install new packages on ubuntu?
any help is greatly appreciated.
here's more info on this topic
[http://liquidweather.net/howto/index.php?id=59](http://liquidweather.net/howto/index.php?id=59)

---

### Post by baseface on 2009-05-18
what shell does root use on ubuntu?
 
```
cat /etc/passwd | grep root
```

---

### Post by junglejuice on 2009-05-18
> **baseface said:**
> what shell does root use on ubuntu?
 
```
cat /etc/passwd | grep root
```

hi
i think it uses dash "dash is a Debian derived light version of bash" as quoated from the website i linked to in my previous post.
thanks

---

