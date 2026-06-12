---
title: "Are Dapper repos out of service?"
date: 2007-01-19
forum: Desktop Environments
---

### Post by Mike_Longbow on 2007-01-19
Hello.
I'm running dapper with xfce and fluxbox, but I've decided to give gnome a try, but when I do:
```
sudo apt-get install ubuntu-desktop
```
aptitude shows that there are a lot of packages to installl, so it starts to download them...
but at some point it stops and tells me:
```
Err http://security.ubuntu.com dapper-security/main firefox-gnome-support 1.5.dfsg+1.5.0.8-0ubuntu0.6.06
  404 Not Found
Err http://archive.ubuntu.com dapper-security/main firefox-gnome-support 1.5.dfsg+1.5.0.8-0ubuntu0.6.06
  404 Not Found [IP: 195.248.90.38 80]
Err http://archive.ubuntu.com dapper-security/main python-uno 2.0.2-2ubuntu12.1
  404 Not Found [IP: 195.248.90.38 80]
Err http://archive.ubuntu.com dapper-security/main openoffice.org-writer 2.0.2-2ubuntu12.1
  404 Not Found [IP: 195.248.90.38 80]
Err http://archive.ubuntu.com dapper-security/main openoffice.org-calc 2.0.2-2ubuntu12.1
  404 Not Found [IP: 195.248.90.38 80]
Err http://archive.ubuntu.com dapper-security/main openoffice.org-math 2.0.2-2ubuntu12.1
  404 Not Found [IP: 195.248.90.38 80]
Err http://archive.ubuntu.com dapper-security/main openoffice.org-java-common 2.0.2-2ubuntu12.1
  404 Not Found [IP: 195.248.90.38 80]
Err http://archive.ubuntu.com dapper-security/main openoffice.org-base 2.0.2-2ubuntu12.1
  404 Not Found [IP: 195.248.90.38 80]
Err http://archive.ubuntu.com dapper-security/main openoffice.org 2.0.2-2ubuntu12.1
  404 Not Found [IP: 195.248.90.38 80]
Err http://archive.ubuntu.com dapper-security/main openoffice.org-evolution 2.0.2-2ubuntu12.1
  404 Not Found [IP: 195.248.90.38 80]
Err http://archive.ubuntu.com dapper-security/main openoffice.org-gtk 2.0.2-2ubuntu12.1
  404 Not Found [IP: 195.248.90.38 80]
Err http://archive.ubuntu.com dapper-security/main openoffice.org-gnome 2.0.2-2ubuntu12.1
  404 Not Found [IP: 195.248.90.38 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-gnome-support_1.5.dfsg+1.5.0.8-0ubuntu0.6.06_i386.deb  404 Not Found [IP: 195.248.90.38 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/python-uno_2.0.2-2ubuntu12.1_i386.deb  404 Not Found [IP: 195.248.90.38 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-writer_2.0.2-2ubuntu12.1_i386.deb  404 Not Found [IP: 195.248.90.38 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-calc_2.0.2-2ubuntu12.1_i386.deb  404 Not Found [IP: 195.248.90.38 80]Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-math_2.0.2-2ubuntu12.1_i386.deb  404 Not Found [IP: 195.248.90.38 80]Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-java-common_2.0.2-2ubuntu12.1_all.deb  404 Not Found [IP: 195.248.90.38 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-base_2.0.2-2ubuntu12.1_i386.deb  404 Not Found [IP: 195.248.90.38 80]Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org_2.0.2-2ubuntu12.1_i386.deb  404 Not Found [IP: 195.248.90.38 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-evolution_2.0.2-2ubuntu12.1_i386.deb  404 Not Found [IP: 195.248.90.38 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-gtk_2.0.2-2ubuntu12.1_i386.deb  404 Not Found [IP: 195.248.90.38 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-gnome_2.0.2-2ubuntu12.1_i386.deb  404 Not Found [IP: 195.248.90.38 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
```
What's wrong with the repos?
And other question... I can use --fix-missing and install the packages I've already downloaded, but I don't know if this one up here are essential to the sytem....
So... What to do? :confused:

---

### Post by PilotJLR on 2007-01-19
The repos are fine. Do this, and then repeat you install command:
```

sudo apt-get update

```

---

### Post by Mike_Longbow on 2007-01-19
Oh, stupid me...
I should have tought about that before...
Hehehe, thanks buddy, that did it. :)

---

### Post by PilotJLR on 2007-01-20
Only reason I know it cause I did it once myself   :-)

---

