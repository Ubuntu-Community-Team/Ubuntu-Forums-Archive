---
title: "Is kiten broken for anyone else?"
date: 2005-06-27
forum: Desktop Environments
---

### Post by Flawed on 2005-06-27
Here's the error message I get:

```
kiten: error while loading shared libraries: libkiten.so.1: cannot open shared object file: No such file or directory
```

Bummer, I really wanted to try this as JWPCE gives me font problems in Wine. Does anyone know how this can be fixed? I tried installing the .deb from [http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Funiverse%2Fk%2Fkdeedu%2Fkiten_3.4.0-0ubuntu1_i386.deb&md5sum=43da788e95018d7695840474adb98703&arch=i386&type=main](http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Funiverse%2Fk%2Fkdeedu%2Fkiten_3.4.0-0ubuntu1_i386.deb&md5sum=43da788e95018d7695840474adb98703&arch=i386&type=main)
but it gives me the same error. Thanks a lot in advance.

---

### Post by argux on 2005-06-27
Thank you, I thought I was the only one to have this problem.

I've searched the debian package page, and that library doesn't seem to be anywhere. At first I thought I needed to install something else, but I figured it should have been done by apt-get, so I maybe it's a bug. I was about to file it, but then I thought I might check the forums first. 

So, does anyone know if this sould be filed? Is it a known problem? I think that if by installing the package it doesn't pull everything that's needed, then it's a bug, am I wrong?

Cheers!

---

### Post by Flawed on 2005-06-28
I think this has already been filed as a bug. [https://launchpad.ubuntu.com/malone/distros/ubuntu/+bugs/+index?batch_start=220&batch_end=240](https://launchpad.ubuntu.com/malone/distros/ubuntu/+bugs/+index?batch_start=220&batch_end=240)

---

