---
title: "Digikam"
date: 2005-07-22
forum: Desktop Environments
---

### Post by alec on 2005-07-22
Hi,
Digikam is not registering plugins such as slideshow.

Synaptic is showing them as installed, but digikam configuration settings do not show them.

Anyone got any  ideas as to how to go about tackling this problem???

Cheers

---

### Post by daigorobr on 2005-07-22
[QUOTE=alec]Hi,
Digikam is not registering plugins such as slideshow.

Synaptic is showing them as installed, but digikam configuration settings do not show them.

Anyone got any  ideas as to how to go about tackling this problem???

Cheers[/QUOTE]
 Hey.

I installed all the three packages and they work:
digikamplugins
digikamimageplugins
kipi-plugins

I'm sure there's some other explanation or workover that's more rational, but...

---

### Post by skyboy on 2005-07-23
Yes there are some troubles with Digikam, 
I downloaded the lastest version of all the package there and use dpgk -i *.deb
try it out :
[http://www.mpe.mpg.de/~ach/kubuntu/hoary/Pkgs.php](http://www.mpe.mpg.de/~ach/kubuntu/hoary/Pkgs.php)

---

### Post by alec on 2005-07-23
That has done it, everything is working. 

Though the deb package command should read;

sudo dpkg -i *.deb

Not dpgk. For anyone else following your excellent advice.

Many thanks for the help.

---

### Post by skyboy on 2005-07-23
Glad it helped :)
Sorry for the mistake, i must have had a glass of wine before :D

---

