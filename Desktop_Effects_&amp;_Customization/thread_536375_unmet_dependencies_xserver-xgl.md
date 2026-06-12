---
title: "unmet dependencies: xserver-xgl"
date: 2007-08-27
forum: Desktop Effects &amp; Customization
---

### Post by Tectuktitlay on 2007-08-27
Hi,

I'm trying to install Compiz, just to impress my friends a bring them over to the linux-side. I've read a lot of threads and how-to's, but i get stuck at this point: I need the xserver-xgl package and apt-get complains as follows:

```
sudo apt-get install xserver-xgl
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  xserver-xgl: Depends: libc6 (>= 2.4-1) but 2.3.6-0ubuntu20.5 is to be installed
E: Broken packages
maarten@darkwood:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
```

I've tried manually downloading and installing a newer version of the package from [http://packages.ubuntu.com/edgy/base/libc6](http://packages.ubuntu.com/edgy/base/libc6) with dpkg, bat that throws my into dependency hell, with all kinds of errors coming up. I had to put the old package back and re-install some other, especially locales.

Supposedly you can get Compiz runnig under Dapper. What am I doing wrong?

Thanx,

Maarten

---

