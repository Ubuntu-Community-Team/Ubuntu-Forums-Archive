---
title: "ClamAV - am i up to date or not?"
date: 2005-05-10
forum: Desktop Environments
---

### Post by Obionekanewbie on 2005-05-10
When I attempt to update clamav I get the following results-
andrew@eboxlinux:~ $ sudo apt-get install clamav
Reading Package Lists... Done
Building Dependency Tree... Done
clamav is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
andrew@eboxlinux:~ $ sudo freshclam
ClamAV update process started at Tue May 10 22:11:54 2005
ERROR: Can't query current.cvd.clamav.net
Reading CVD header (main.cvd): OK
main.cvd is up to date (version: 31, sigs: 33079, f-level: 4, builder: tkojm)
WARNING: Your ClamAV installation is OUTDATED - please update immediately!
WARNING: Current functionality level = 3, required = 4
ERROR: Can't query current.cvd.clamav.net
Reading CVD header (daily.cvd): OK

if i do a version check i get :  clamscan -V
ClamAV 0.80/875/Tue May 10 12:27:59 2005

Thanks in advance. :razz:

---

### Post by nocturn on 2005-05-11
> 
andrew@eboxlinux:~ $ sudo freshclam
ClamAV update process started at Tue May 10 22:11:54 2005
ERROR: Can't query current.cvd.clamav.net
Reading CVD header (main.cvd): OK
main.cvd is up to date (version: 31, sigs: 33079, f-level: 4, builder: tkojm)
WARNING: Your ClamAV installation is OUTDATED - please update immediately!
WARNING: Current functionality level = 3, required = 4
ERROR: Can't query current.cvd.clamav.net
Reading CVD header (daily.cvd): OK

if i do a version check i get :  clamscan -V
ClamAV 0.80/875/Tue May 10 12:27:59 2005

Thanks in advance. :razz:

The latest version is "clamav 0.84 released (Fri, 29 Apr 2005 18:12:12 GMT)"
I guess that is the problem.

Ubuntu tracks the debian packages, I guess they're a little behine on this.
Someone at Debian maintains up-to-date packages it seems, check this:

[quote=www.clamav.net]
 Debian

    * The Debian package is maintained by Stephen Gran. ClamAV has been officially included in the Debian distribution starting from the sarge release. Run apt-cache search clamav to find the name of the packages available for installation. Unofficial packages for woody and sarge are available. They are usually more recent than official ones. Add the following lines to your /etc/apt/sources.list:

      stable/woody (i386):
      deb [http://people.debian.org/~sgran/debian](http://people.debian.org/~sgran/debian) woody main
      deb-src [http://people.debian.org/~sgran/debian](http://people.debian.org/~sgran/debian) woody main
      testing/sarge (i386):
      deb [http://people.debian.org/~sgran/debian](http://people.debian.org/~sgran/debian) sarge main
      deb-src [http://people.debian.org/~sgran/debian](http://people.debian.org/~sgran/debian) sarge main
      Feel free to search for clamav on [http://www.apt-get.org](http://www.apt-get.org) too.
[/quote]

---

### Post by Klunk on 2005-05-13
I am running Hoary and have everything updated but running freshclam gives the following warning.

> WARNING: Local version: 0.83 Recommended version: 0.85

---

### Post by stubby on 2005-05-15
[QUOTE=Klunk]I am running Hoary and have everything updated but running freshclam gives the following warning.[/QUOTE]

I get the same error message. Does anyone know where to get the latest .deb package of ClamAV from ?

---

### Post by Klunk on 2005-05-16
I have just added the Debian Woody repository listed [here](http://www.clamav.net/binary.html#pagestart) to my sources and pulled the latest version from there. I am now up to date.

HTH.

---

