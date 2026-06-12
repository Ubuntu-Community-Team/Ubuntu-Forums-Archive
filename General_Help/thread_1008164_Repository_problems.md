---
title: "Repository problems"
date: 2008-12-11
forum: General Help
---

### Post by nimonika on 2008-12-11
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/edgy-backports/main/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/edgy-backports/main/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/edgy-backports/restricted/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/edgy-backports/restricted/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/edgy-backports/universe/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/edgy-backports/universe/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/edgy-backports/multiverse/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/edgy-backports/multiverse/binary-i386/Packages.gz)  404 Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

Please can someone advise what to do here.

Thanks

---

### Post by kgas on 2008-12-11
Hello try to change your sources thro' System->Administration->software source. and also you can check the fast mirrors near by you.

---

### Post by Michael.Godawski on 2008-12-11
[FONT=Lucida Sans Unicode]hi nimonika, 
[http://gb.archive.ubuntu.com/ubuntu/dists/](http://gb.archive.ubuntu.com/ubuntu/dists/)
there is no edgy repository on this server, try to change the server and run

```
sudo apt-get update
sudo apt-get upgrade
```[/FONT]

---

